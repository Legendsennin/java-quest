# World 5: Spring Boot City

**Story**: welcome to the city where real backends live. Spring Boot runs the backend of the project you'll join. Here you build your own API from nothing, test it with Postman, and learn to read logs like a pro.
**Cool build**: a **Quest Board API**: create, list, update and complete quests over HTTP, stored in a database, with validation, proper error codes, tests, and a Postman collection.
**Code lives in** `workbench/quest-board/`, its own new Git repo (G5.1).
**Power-up: Pilot.** You write 4-part prompts; the AI implements steps; you review every changed line and run the tests.
**Versions**: match the Java and Spring Boot versions of the team's project (PRISM) when known; otherwise Java 21 + the latest Spring Boot. Tutorials written before Spring Boot 3 use `javax.*`; new code uses `jakarta.*`. Spot it and say so.

## Quests

| ID | Quest | Concepts | Build step |
|---|---|---|---|
| Q5.1 | How the Web Talks | HTTP request/response, methods (GET/POST/PUT/DELETE), status codes, JSON, URL anatomy | read real requests in the browser's dev tools |
| Q5.2 | Hello, Spring | start.spring.io, project structure, `main`, `@RestController`, `@GetMapping`, the first Postman request + a status test | `GET /ping`. Achievement **Special Delivery** |
| Q5.3 | The Restaurant | layers: controller → service → repository; dependency injection through the constructor | the Quest Board skeleton |
| Q5.4 | The Vault | JPA `@Entity`, repository interfaces, H2 database, `@RequestBody`, `@PathVariable` | save and load quests |
| Q5.5 | Bouncers | validation (`@Valid`, `@NotBlank`), 400 vs 404 vs 500, `@RestControllerAdvice` | reject bad quests with clear errors |
| Q5.6 | Control Room | `application.yml` / `.properties`, profiles, log levels, reading startup and request logs | trace one request through the logs |
| Q5.7 | Magic Revealed | Lombok (`@Getter`, `@Builder`, `@RequiredArgsConstructor`): what it writes for you | delete boilerplate you once wrote by hand |
| Q5.8 | Proof | unit tests with Mockito vs `@SpringBootTest` vs MockMvc | test the endpoints |

## Explain recipes

- **HTTP**: ordering at a restaurant. The request is the order slip (method + URL + body); the response is the plate plus a status: 200 "here you go", 400 "we can't read your order", 404 "not on the menu", 500 "the kitchen caught fire".
- **Layers**: the **controller** is the waiter (takes the order, returns the plate, doesn't cook), the **service** is the chef (the business rules), the **repository** is the pantry keeper (fetches and stores ingredients), and the **database** is the warehouse. Where it breaks: in real apps one request may visit several chefs.
- **Dependency injection**: Spring is the game engine. At startup it spawns every object it manages (a "bean") and hands each one the objects it asks for in its constructor. You declare what you need; the engine wires it up.
- **Annotations**: labels that tell Spring what a class is for, like `@RestController`, `@Service`, `@Repository`.
- **Lombok**: code generated at compile time. Only show it after the player has written getters and constructors by hand (W3), so it's a shortcut, not magic.

## Challenge focus

- **Predict the Response**: given a request and the code, predict the status code and JSON before sending it in Postman.
- **Layer Detective**: given a feature, the player says which layer each piece of code belongs in.
- **Bug Hunts**: a 404 from a wrong path, a 400 from validation, a 500 whose cause is in the logs.

## Git quests: a real project's history

| ID | When | Quest | Commands |
|---|---|---|---|
| G5.1 | Q5.2 | **New Repo, Real Project**: the Spring app gets its own repo, from scratch, from memory | `git init`; `.gitignore` from the github/gitignore templates (Gradle or Maven, plus IDE files) + `.env`; first commit; an EMPTY GitHub repo `quest-board`; `git remote add origin`; `git push -u origin main` |
| G5.2 | Q5.6 | **Secrets Stay Home**: passwords and keys come from environment variables or an ignored local file (e.g. `application-local.yml`), never from committed files | `.gitignore`; `git log -S "password"` in a leaked-secret kata; deleting a secret in a new commit doesn't remove it from history, so the fix is to change the secret |
| G5.3 | every quest | **One Endpoint, One PR**: each quest = one branch + one PR, ideally under about 100 changed lines, with its Postman requests saved in the repo | the GitHub flow in `game/playbooks/git.md` |
| G5.4 | hard path | **Tidy Before Review**: rebase your own branch onto the new `main`, or squash WIP commits, but only commits never pushed. Backup branch first | `git branch backup/<name>`, `git rebase main`, `git rebase -i main`, `git rebase --abort` |
| Side | hard path | **Robots on Guard**: a GitHub Actions workflow that runs the tests on every PR, then make it a required check in the ruleset | `.github/workflows/test.yml` |

- Pro Git's rule for rebase: "Do not rebase commits that exist outside your repository and that people may have based work on." Many teams merge instead of rebasing; know both, and follow the team's rule.
- GitHub scans public repos for leaked secrets and blocks many pushes that contain them. It's a safety net, not a guarantee.

## Boss: The Request

1. Predict the status code and JSON for 5 unseen requests: 4 correct.
2. State the job of each layer in one line.
3. Add a new endpoint with a test, using hints only (the AI may not write it). It arrives through a pull request: clean history, good messages, and no secrets anywhere in `git log -p`.

Unlocks W6 The Real Job and the **Commander** power-up.

**The nudge** starts here: when the player mentions a PRISM task, suggest trying it in Work Mode (AGENTS.md section 9).
