# World 4: Guild of Contracts

**Story**: big games are built by many teams who agree on contracts: "anything that can attack must have an `attack()` method." Contracts let parts plug together without knowing each other's insides. Spring Boot is built on this idea.
**Cool build**: a **Battle System**: warriors, mages and monsters that all fight through one contract, loot filters, and a test suite that proves the battle math.
**Code lives in** `workbench/java-basics/w4/`, now as a real Maven or Gradle project (use whichever the team's project uses).
**Power-up: Co-pilot.** The AI may generate code *after* you write the plan; you modify it and explain every line. Code you can't explain doesn't go in.
**Where this shows up at work**: Spring uses interfaces everywhere (repositories are interfaces you never implement yourself), streams and lambdas are in almost every service, and tests are how teams change code without fear.

## Quests

| ID | Quest | Concepts | Build step |
|---|---|---|---|
| Q4.1 | The Contract | `interface`, `implements`, polymorphism | `Attacker`: `Warrior` and `Mage` |
| Q4.2 | Family Trees | `extends`, `abstract` class, `@Override`, `super`; interface vs abstract class | a `Monster` base class |
| Q4.3 | Loot Boxes | generics: `List<Item>`, writing your own `Box<T>` | a typed loot box |
| Q4.4 | Combo Moves | lambdas, method references, functional interfaces | pass a skill around as a value |
| Q4.5 | Loot Filters | streams: `filter`, `map`, `sorted`, `collect`; `Optional` | top 3 epic items; a chest that may be empty |
| Q4.6 | Rarity & Records | `enum`, `record`, `switch` expressions | `Rarity` enum, `Item` record |
| Q4.7 | Green Bar | JUnit 5, the build tool (Maven/Gradle), packages and imports | tests for the battle math. Achievement **Green Bar** |

## Explain recipes

- **Interface**: a controller port. Any gamepad that fits the port works, and the console doesn't care which brand it is.
- **Polymorphism**: one button, "attack", and each class does its own version.
- **Generics**: a loot box labelled with what's inside, so the compiler stops you from putting a potion in a sword box.
- **Lambda**: a skill you can pass around like an item and use later.
- **Stream**: a conveyor belt of machines: filter → transform → collect.
- **`Optional`**: a chest that might be empty. You must check before grabbing.
- **Test**: an automatic referee that re-checks the rules every time you change code.

## Challenge focus

- **Why-This-Not-That Duels**: interface vs abstract class; loop vs stream; `record` vs class.
- **Almost-Right Hunts** on AI-generated streams (wrong `sorted` order, a forgotten empty case).
- **PRIMM Modify**: take working, tested code and change its behaviour while keeping the tests green.

## Git quests: pull requests

From here on, work reaches `main` through pull requests (PRs), like on a real team.

| ID | When | Quest | Commands |
|---|---|---|---|
| G4.1 | Q4.1 | **Pull Requests**: branch → push → open a PR on GitHub → review your own diff → merge → clean up | `git switch -c feature/q4-1-contracts`, `git push -u origin feature/q4-1-contracts`, `git diff main...HEAD`; on GitHub: New pull request, description, Merge; then `git switch main`, `git pull`, `git branch -d feature/q4-1-contracts`, `git fetch --prune` |
| G4.2 | Q4.2 | **Guard the Main**: a GitHub ruleset on `main` that requires a pull request and blocks force pushes. Then try pushing straight to `main` and read the refusal | GitHub: Settings → Rules → Rulesets |
| G4.3 | Q4.5 | **Pocket Dimension**: mid-quest, Byte reports an urgent bug on `main` | `git stash push -u -m "WIP loot filters"`, `git switch -c fix/… main`, fix, PR, merge, `git switch -`, `git stash list`, `git stash pop` |
| G4.4 | Q4.7 | **Commit Craft**: split work into small commits with messages that say why; add the github/gitignore templates for Java + Maven/Gradle | `git add -p`, a message with a body (`git commit` opens VS Code) |
| G4.5 | end of W4 | **Release**: tag the finished battle system | `git tag -a v0.1.0 -m "Battle system"`, `git push origin v0.1.0`; SemVer: MAJOR.MINOR.PATCH |

- A PR description says what changed, why, and how it was tested. "Closes #3" closes issue 3 when the PR merges into the default branch.
- Review your own PR with the checklist in `game/playbooks/git.md` before merging. Small PRs are easier to review: aim for about 100 changed lines.
- Combining the Java and Gradle templates: Gradle's `!gradle-wrapper.jar` line must come after Java's `*.jar`, or the wrapper gets ignored.
- A dropped stash is hard to get back. A "WIP" commit on your branch is a safer pocket.
- Achievement: **Merged** (first PR merged).

## Boss: The Contract

1. Explain 4 of 5 unseen 15–25 line classes or methods, each in one sentence of purpose.
2. A Modify task on unseen code, finished with all tests green.
3. **Git round**: deliver the Modify task through a pull request: branch, small commits with good messages, PR description, self-review, merge, clean-up.

No hints. Unlocks W5 Spring Boot City and the **Pilot** power-up.
