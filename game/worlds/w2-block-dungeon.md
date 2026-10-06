# World 2: Block Dungeon

**Story**: atoms combine into blocks, small groups of lines that do one job. Pros read code block by block, not line by line. That's how they read fast.
**Cool build**: an **Inventory Manager**: total gold, the heaviest item, find the key, filter out the junk, and a damage calculator you can reuse.
**Code lives in** `workbench/java-basics/w2/`. From now on, every quest gets its own branch.
**Where this shows up at work**: most business code is these patterns in disguise: totals, searches, maximums, filters.

## Quests

| ID | Quest | Concepts | Build step |
|---|---|---|---|
| Q2.1 | The Inventory Bar | arrays: index 0, `length`, out of bounds | inventory slots |
| Q2.2 | Running Totals | accumulator pattern: sum, count, average | total gold, potion count |
| Q2.3 | King of the Hill | max/min, search with a flag, stopping early | strongest item, find the key |
| Q2.4 | Spells | methods: parameters, return values, `void`, scope | `damage()` and `heal()` |
| Q2.5 | Switch & Grids | `switch` arrow form, nested loops, 2D arrays | class bonus, a dungeon grid |
| Q2.6 | Refactor Room | naming, extracting methods, one method = one job | clean up Byte's 60-line mess |

## Explain recipes

- **Accumulator**: a running score counter that starts at 0 and adds as you go.
- **Max pattern**: king of the hill. Assume the first is king; any challenger that's bigger takes the crown.
- **Method**: a spell you define once and cast many times. Parameters are what you feed it; the return value is what it gives back.
- **Subgoal labels**: before writing, the player names the steps (for example: set up → loop → update → return). Then compare with yours.

## Challenge focus

- **One-Sentence Summary** after every quest. Line-by-line narration = "not yet"; a sentence that names the goal = pass.
- **Code Shuffle** with one distractor line.
- **Name That Pattern**: show a block; the player names the pattern (accumulator, max, search, filter).

## Git quests (woven between the Java quests)

Before every `git graph`, the player predicts (or sketches) the graph.

| ID | When | Quest | Commands | Picture |
|---|---|---|---|---|
| G2.1 | start of Q2.1 | **Sticky Labels**: one branch per quest, from now on | `git branch`, `git switch -c quest/q2-1-inventory`, `git switch main`, `git switch -`, `git graph` | labels |
| G2.2 | end of Q2.1 | **Join the Lines**: a fast-forward merge (the label just slides forward) | `git switch main`, `git merge quest/q2-1-inventory`, `git branch -d quest/q2-1-inventory`, `git push` | labels |
| G2.3 | during Q2.3 | **Two Paths**: a commit on `main` (a README change) AND on the quest branch, so the merge makes a commit with two parents | `git merge`, `git graph` | labels |
| G2.4 | Q2.6 Refactor Room | **First Conflict**: Byte changed the same line on `main` | `git config --global merge.conflictstyle zdiff3`, `git status`, edit the markers by hand or in VS Code's merge editor, `git add`, `git commit`; the exit: `git merge --abort`; the check: `git diff --check` | conflict |
| G2.5 | any time after G2.2 | **Undo, Rung 1** (local only) | `git restore --staged <file>`, `git restore <file>` (RED), `git commit --amend` (only if not pushed) | safety colours |

- G2.4 setup: the player switches to `main`; you (as Byte) change one line in their file; they commit it as "Byte: rename potion constant". Then they merge their Refactor Room branch, which changed the same line.
- A conflict is a question, not a crash: Git asks "which version do you want?"
- Achievements: **Branch Out** (first merge), **Peacemaker** (first conflict resolved).

### Git misconception probes

- "A branch is a folder or a copy of the project." → What changed on disk after `git branch x`?
- "HEAD is the newest commit." → After `git switch main`, what does HEAD point to?
- "Uncommitted edits stay on the branch where I made them." → Edit on `main`, switch branches: where's the edit?
- "A conflict means Git broke; start again." → What moves finish or cancel a merge?

## Boss: The Summariser

1. Explain 4 of 5 unseen 8–12 line blocks, each in one sentence that states the purpose.
2. Code Shuffles with distractors: 80% or more right first try.
3. **Git round**: Match the Target Graph in a dojo kata (a branch merged into `main`, plus one more commit), then a Conflict Duel kata.

No hints. Unlocks W3 Object Kingdom and the **Explain-o-scope** power-up: the AI may now show example code, and you predict what it does before it runs.
