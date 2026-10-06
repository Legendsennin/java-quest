# World 3: Object Kingdom

**Story**: until now, data floated around loose. Now it gets bodies: objects with their own stats and abilities, living in memory. This is the world where Java starts to look like real software.
**Cool build**: an **RPG Party**: `Hero` objects with protected stats, a party list, an inventory bag, and the infamous Shared Potion bug.
**Code lives in** `workbench/java-basics/w3/`.
**Tool**: Java Visualizer (https://cscircles.cemc.uwaterloo.ca/java_visualize/) shows the stack and heap step by step. The player sketches memory first, then checks it there.
**Where this shows up at work**: every entity, DTO and service in a Spring app is a class, and most real bugs are about `null` and references.

## Quests

| ID | Quest | Concepts | Build step |
|---|---|---|---|
| Q3.1 | Character Creator | class vs object, fields, constructor, `new` | the `Hero` class |
| Q3.2 | Guarded Stats | methods, `this`, `private` + getters/setters (encapsulation) | HP can never go negative |
| Q3.3 | The Memory Map | stack vs heap, references, aliasing | the Shared Potion bug |
| Q3.4 | The Empty Slot | `null`, NullPointerException, `==` vs `equals` | two identical swords |
| Q3.5 | World Rules | `static` vs instance | `MAX_LEVEL`, a hero counter |
| Q3.6 | Party & Bag | `ArrayList`, `HashMap`, looping over collections | the party list and inventory map |
| Q3.7 | Traps | exceptions: `throw`, `try`/`catch`, checked vs unchecked, a first stack trace | a bad potion throws |

## Explain recipes

- **Class vs object**: the class is the character-creator screen; each object is a character you actually created. One template, many characters.
- **Reference**: a variable doesn't hold the object itself; it holds directions to it, like a party slot that points to a character. Two slots can point to the same character. That's aliasing, and it's the Shared Potion bug.
- **`==` vs `equals`**: two swords with identical stats are *equal* but not the *same* sword. `==` asks "same object?"; `equals` asks "same content?".
- **`null`**: an empty party slot. Calling a method on it is like ordering an empty slot to attack.
- **`static`**: belongs to the game world (one copy), not to each character.

## Misconception probes (use as Predict the Output + a heap sketch)

- `Hero a = new Hero("Aria"); Hero b = a; b.setHp(1);` → `a` also has 1 HP.
- `new String("sword") == new String("sword")` → `false`; `.equals(...)` → `true`.
- A method that reassigns its parameter doesn't change the caller's variable; a method that changes a field of the object passed in does (Java passes references by value).
- Calling a method on a `null` variable → NullPointerException. Where the null came from matters more than where it crashed.
- Changing a `static` field through one object changes it for every object.

## Git quests: working with a remote

Until now GitHub was a backup. Now it's a place where changes also come FROM, like on a team.

| ID | When | Quest | Commands | Picture |
|---|---|---|---|---|
| G3.1 | start of W3 | **Postcards**: `origin/main` is what GitHub looked like the last time you checked, not live | `git fetch`, `git status -sb` (ahead/behind), `git branch -vv` | remotes |
| G3.2 | during Q3.2 | **A Teammate Appears**: "Byte" (the player, on github.com) edits a file; the player also commits locally; the push gets rejected | `git push` (rejected: read the message), `git fetch`, `git merge origin/main`, resolve if needed, `git push` | remotes |
| G3.3 | during Q3.6 | **Second PC**: clone the repo into `workbench/second-pc/`, commit and push there, then pull in the first folder | `cd` to the java-quest folder, then `git clone <url> workbench/second-pc`; `git pull` | remotes |
| G3.4 | during Q3.3 | **Spectator Mode**: visit an old save point, look around, come back | `git log --oneline`, `git switch --detach <hash>`, `git switch main`; keep commits made there with `git switch -c <name>` | labels |
| G3.5 | during Q3.7 | **Flight Recorder**: the "vanished-commits" kata (setup script in `game/playbooks/git.md`) | `git reflog`, `git branch rescue <hash>`; what `git reset --hard` does (RED) | safety colours |

- The #1 beginner mistake teachers see is pushing before pulling (Software Carpentry instructor notes). G3.2 makes it happen on purpose, safely.
- Delete `workbench/second-pc/` after G3.3.
- Achievement: **Lost and Found** (G3.5).

### Git misconception probes

- "`origin/main` is live GitHub." → When was it last updated?
- "fetch and pull are the same thing." → Which one can change your files?
- "Committed work is fragile; uncommitted work is safe." → What can the reflog NOT bring back?
- "Detached HEAD means something broke." → How do you keep commits made there?

## Boss: The Memory Map

1. Stack/heap sketches for 7 unseen aliasing and parameter snippets: 6 correct, checked in Java Visualizer.
2. Misconception probes: 90% or more.
3. **Git round**: Undo Roulette (4 situations: pick the safe undo and say why), then a fresh Rescue Mission kata.

No hints. Unlocks W4 Guild of Contracts and the **Co-pilot** power-up.
