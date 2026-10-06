# Playbook: debugging

Debugging is a process you can learn, not a talent. Teaching a systematic debugging process explicitly has been shown to raise both debugging performance and confidence (Michaeli & Romeike 2019).

## The Debug Loop (the scientific method, from Zeller's Debugging Book)

1. **Reproduce**: make it fail on purpose, the same way, every time (a Postman request, a test, or exact steps).
2. **Evidence**: the error message, stack trace, logs, and the input that triggers it.
3. **Hypothesis**: "I think X happens because Y."
4. **Prediction**: "If that's true, then when I do Z, I'll see W."
5. **One experiment**: change or print ONE thing.
6. **Log it**: write down hypothesis → result. A debug log beats memory.
7. **Fix only when you can explain the cause**: why it broke and why the fix works. Changing random things until it works is "debugging into existence".
8. **Regression test**: a test that fails without the fix and passes with it.

## Compiler errors (W1+)

Compiler messages are hard for everyone at first; research agrees they're especially hard for beginners. Reading them is a trainable skill.

| Message | Plain words | Usual cause |
|---|---|---|
| `cannot find symbol` | "I don't know that name" | typo, wrong capital letter, variable declared inside another block, missing import |
| `incompatible types` | "wrong shape for this slot" | a `String` into an `int`, a `double` into an `int` |
| `';' expected` | "your sentence didn't end" | missing semicolon, often on the line *above* the one reported |
| `missing return statement` | "one path doesn't give an answer back" | an `if` that returns, with no `return` for the other case |
| `class X is public, should be declared in a file named X.java` | "file name and class name must match" | renamed the class but not the file |

## Reading a stack trace (W3+)

Simplified example:

```
java.lang.IllegalStateException: Could not load hero 7          <- 1. first line: WHAT happened
    at com.guildhall.hero.HeroController.get(HeroController.java:27)
    at org.springframework....                                   (framework lines: skip)
Caused by: java.lang.NullPointerException: Cannot invoke "Guild.getName()"
    because the return value of "Hero.getGuild()" is null         <- 2. LAST "Caused by": the root cause
    at com.guildhall.hero.HeroService.describe(HeroService.java:42)   <- 3. first line in OUR code: start here
    at com.guildhall.hero.HeroController.get(HeroController.java:25)
```

Order: (1) the first line: exception type + message; (2) the last "Caused by": the real root cause; (3) the first `at ...` line in our own packages, skipping framework lines.

## Common runtime exceptions

| Exception | Meaning | First question |
|---|---|---|
| `NullPointerException` | used something that's `null` | where did the null *come from*? |
| `ArrayIndexOutOfBoundsException` / `IndexOutOfBoundsException` | index outside 0 to length − 1 | off-by-one? empty list? |
| `NumberFormatException` | the text isn't a number | what exact string came in? |
| `ClassCastException` | treated an object as a type it isn't | where was it created? |
| `IllegalArgumentException` / `IllegalStateException` | code rejected bad input or state on purpose | read the message: someone left you a note |

## Spring Boot classics (W5+)

| Symptom | Usual cause |
|---|---|
| `Port 8080 was already in use` | the app is already running in another terminal: stop it or change `server.port` |
| `required a bean of type '...' that could not be found` | class missing `@Service` / `@Repository` / `@Component`, or outside the main application's package |
| `Failed to configure a DataSource` | a JPA starter with no database settings |
| Whitelabel Error Page, 404 | wrong path or HTTP method, or the controller isn't being picked up |
| 400 Bad Request | the JSON doesn't match the request class, or validation failed |
| 500 Internal Server Error | a server-side exception: the stack trace is in the logs |

## HTTP triage

- **4xx** → suspect the request: URL, method, headers, body. (401 = not logged in; 403 = logged in but not allowed; 404 = no such thing.)
- **5xx** → suspect the server: read the logs.

## Reading logs

- Levels: `ERROR` > `WARN` > `INFO` > `DEBUG` > `TRACE`. Start at the ERROR, then read around it.
- Order: the **time** of the failure → the **request** (path, id) → the **stack trace** → the last "Caused by".
- Search the log for the ID of the thing that failed (hero id, request id).

## Tracing with a variable table

When code "should work" but doesn't: go line by line and write every variable's value after each line in a table. A 5–10 minute tracing strategy like this raised novices' tracing scores by 15% (Xie et al. 2018).

## Asking AI for debugging help (pilot style)

Mask first: replace names, IC numbers, account numbers and tokens with `<NAME>`, `<IC>`, `<ACCOUNT>`, `<TOKEN>`.

```
Goal: find why GET /heroes/7 returns 500.
Context: Spring Boot <version>. HeroService.describe(); stack trace below (masked).
Expected: 200 with the hero's JSON. Actual: 500, NullPointerException at HeroService.java:42.
Tried: checked that hero 7 exists in the database (it does).
Ask: give me 3 hypotheses ranked by likelihood and how to test each. Don't write the fix.
```
