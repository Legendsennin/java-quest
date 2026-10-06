# World 1: Atom Valley

**Story**: everything in software is built from tiny atoms: values, variables and simple steps. Master them and no code will ever look like magic again.
**Cool build**: a **Loot Drop Generator**. Roll a random number, turn it into a rarity (common, rare, epic, legendary), open 10 chests, and count the legendaries.
**Tools**: `jshell` for quick experiments. Single files run with `java LootDrop.java` (no project needed). Code lives in `workbench/java-basics/w1/` (the `java-basics` repo, created in G1.1).
**Where this shows up at work**: every backend calculates things (fees, dates, counters, limits) with exactly these atoms.

## Quests

| ID | Quest | Concepts | Build step |
|---|---|---|---|
| Q1.1 | Values & Variables | `int`, `double`, `boolean`, `String`; declaring and assigning; a variable holds ONE value at a time; how Java runs (source → compiler → bytecode → JVM) | store a hero's stats |
| Q1.2 | Operators & Surprises | `+ - * / %`, integer division (`7 / 2` is `3`), remainder, `String` + number | damage and critical-hit math |
| Q1.3 | Decisions | `if` / `else if` / `else`, comparisons, `&&` `\|\|` `!`, `=` vs `==` | rarity from a roll |
| Q1.4 | Loops | `while`, `for`, counting, off-by-one | open 10 chests |
| Q1.5 | Talking to Java | calling methods: `Math.random()` / `Random`, `String` methods (`length`, `toUpperCase`, `contains`), `println` vs `print` | the full Loot Drop Generator |
| Q1.6 | Error Whisperer | reading compiler errors: `cannot find symbol`, `incompatible types`, `';' expected`, `missing return statement` | fix Byte's broken loot code |

Scaffolding for Q1.5: give a file with the structure done and `// TODO(you)` blanks for the rarity logic and the counting loop.

## Explain recipes

- **Variable**: start with "a labelled box holding one value". At the first reassignment, switch to "a name tag that moves to a new value", and say why: a box suggests it keeps the old value too. (Hermans et al. 2018)
- **Integer division**: have them predict `7 / 2` before running it. The surprise is the hook.
- **`=` vs `==`**: "`=` puts a value in; `==` asks a question."
- **Loops**: a respawn timer or a game loop. Use a trace table every time.
- **The JVM**: Java compiles to bytecode that runs on the Java Virtual Machine, a bit like a game that runs on any console that has the right emulator.

## Misconception probes (use as Predict the Output)

- `int x = 5; x = 7;` → `x` is 7 only, not both.
- `int a = 3; int b = a; a = 10;` → `b` is still 3.
- `7 / 2` is `3`; `7 / 2.0` is `3.5`; `7 % 2` is `1`.
- `"1" + 2 + 3` is `"123"`; `1 + 2 + "3"` is `"33"`.
- `for (int i = 0; i <= 3; i++)` runs 4 times.
- `if (x = 5)` doesn't compile in Java. Ask why before explaining.

## Git quests (woven between the Java quests)

| ID | When | Quest | Commands | Picture |
|---|---|---|---|---|
| G1.1 | before Q1.1's code | **The Vault**: make `workbench/java-basics` a repo, and add a `.gitignore` before anything else (`*.class`, `out/`, `.env`) | `mkdir -p`, `cd`, `git init`, `ls -a` (meet `.git`), `git status` | the three areas |
| G1.2 | after Q1.1 | **First Save Point** | `git add <file>` (by name, not `git add .`), `git status`, `git diff --cached`, `git commit` (first message rules) | snapshots |
| G1.3 | after Q1.2 | **Spot the Difference**: two diffs, and the history | `git diff`, `git diff --staged`, `git log --oneline`, `git show` | snapshots |
| G1.4 | after Q1.5 | **Uplink**: publish to GitHub, then a web edit comes back down | create an EMPTY public repo `java-basics` (no README, licence or .gitignore); `git remote add origin <https-url>`, `git remote -v`, `git push -u origin main`; edit README.md on github.com, then `git pull` | remotes |

- G1.4's first push opens a browser window to sign in (Git Credential Manager, installed with Git). No password typing in the terminal.
- **Habits from here on**: commit after every quest step that works; from G1.4 on, push at the end of every session. Read `git diff --cached` before every commit.
- Achievements: **Git Gud** (first commit), **Uplink** (first push).

### Git misconception probes

- "I saved in the editor, so Git has it." → Which of the three areas holds this edit right now?
- "`git add` means 'track this file' forever." → You edited it again after `git add`. What will the commit contain?
- "A commit uploads my work." → Can anyone else see it yet? Which command changes that?
- "Git and GitHub are the same thing." → Can you commit with the Wi-Fi off?

## Boss: The Tracer

10 unseen 5–10 line snippets mixing everything in W1. The player predicts final values and output with a trace table.
Pass: 8 of 10, no hints. Retries are free and unlimited, with new snippets each time. Rematch 7+ days later.
**Git round**: predict what `git status` says in 3 situations (file edited, file staged, file committed), and `git status -sb` shows all W1 work pushed.
Unlocks W2 Block Dungeon.
