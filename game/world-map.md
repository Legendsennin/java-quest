# World map

## The journey

```
[W0 Pilot Academy] -> [W1 Atom Valley] -> [W2 Block Dungeon] -> [W3 Object Kingdom]
   -> [W4 Guild of Contracts] -> [W5 Spring Boot City] -> [W6 The Real Job]
   -> [W7 Architect's Tower] -> ~ ~ ~ fog: New Game+ regions ~ ~ ~
```

| World | You learn | Reading level | AI power-up | Boss gate (beat it to unlock the next world) |
|---|---|---|---|---|
| W0 Pilot Academy | Setup, how to work with AI, prompting | — | Tutor | **Pilot License**: explain pilot vs passenger with one real data point, write a 4-part prompt, state your top 3 pilot rules |
| W1 Atom Valley | Values, variables, types, operators, if/else, loops, method calls, compiler errors | Atoms: trace what each line does | Tutor | **The Tracer**: predict 8 of 10 unseen 5–10 line snippets with a trace table, no hints |
| W2 Block Dungeon | Arrays, patterns (sum, count, max, search), methods, switch, nested loops | Blocks: what a group of lines achieves | Tutor | **The Summariser**: explain 4 of 5 unseen 8–12 line blocks in one sentence (purpose, not line by line) + 80% of Code Shuffles right first try |
| W3 Object Kingdom | Classes, objects, references, null, `equals`, static, collections, exceptions, git save points | Relations in memory | Explain-o-scope | **The Memory Map**: correct stack/heap sketch for 6 of 7 snippets + 90% on misconception probes |
| W4 Guild of Contracts | Interfaces, inheritance, generics, lambdas, streams, Optional, records, enums, JUnit, build tools | Relations between parts | Co-pilot | **The Contract**: explain 4 of 5 unseen 15–25 line classes in one sentence + finish a Modify task with tests green |
| W5 Spring Boot City | HTTP, JSON, Postman, controllers, services, repositories, DI, JPA, validation, errors, config, logs, tests | Macro: one request end to end | Pilot | **The Request**: predict status + JSON for 4 of 5 requests; say each layer's job in one line; add an endpoint + test with hints only |
| W6 The Real Job | Existing codebase, Jira stories, bugs, features, logs, git branches, PRs, code review | Macro: a real codebase | Commander | **The Case File**: fix a fresh dungeon bug end to end: reproduce, hypothesis log, fix, regression test, explain every line, PR text |
| W7 Architect's Tower | Reading top-down, design patterns, Spring's hidden machinery, transactions, security chain, testing strategy, design trade-offs | Macro: design | Commander | **The Architect**: 5-sentence summary of an unfamiliar feature (goal, flow, decision, alternative, consequence) confirmed by a trace + win a design duel |

Every boss comes back for a **rematch** 7+ days after the win. Winning again earns rematch XP and proves the skill stuck.

## Git track (woven into every world)

Git is learned where the code needs it, not saved for the end. Each world file says when each G-quest happens; the rules and pictures are in `game/playbooks/git.md`.

| World | Git quests | Git round in the boss |
|---|---|---|
| W0 | G0.1 Terminal Basics · G0.2 Guild Registration (GitHub account, 2FA, private email) · G0.3 Sign Your Work (settings) | Setup check |
| W1 | G1.1 The Vault (init, .gitignore) · G1.2 First Save Point (add, commit) · G1.3 Spot the Difference (diff, log, show) · G1.4 Uplink (first push; a web edit comes back with pull) | Predict `git status` in 3 situations; all W1 work pushed |
| W2 | G2.1 Sticky Labels (branches) · G2.2 Join the Lines (fast-forward merge) · G2.3 Two Paths (merge commit) · G2.4 First Conflict · G2.5 Undo, Rung 1 | Match the Target Graph + Conflict Duel |
| W3 | G3.1 Postcards (fetch, origin/main) · G3.2 A Teammate Appears (rejected push) · G3.3 Second PC (clone) · G3.4 Spectator Mode (detached HEAD) · G3.5 Flight Recorder (reflog rescue) | Undo Roulette + Rescue Mission |
| W4 | G4.1 Pull Requests · G4.2 Guard the Main (ruleset) · G4.3 Pocket Dimension (stash) · G4.4 Commit Craft · G4.5 Release (tags, SemVer) | A quest delivered through a PR, no hints |
| W5 | G5.1 New Repo, Real Project · G5.2 Secrets Stay Home · G5.3 One Endpoint, One PR · G5.4 Tidy Before Review (rebase, own branch only) · Side: Robots on Guard (CI) | The boss endpoint arrives through a clean PR, no secrets |
| W6 | G6.1 Red Build on Day One (revert) · G6.2 History Detective (blame, log -S) · G6.3 Ticket Branches (PRs on a team repo) · G6.4 Review Round-trip (draft PR, review fixes, merge method) · G6.5 Bisect Hunt · G6.6 Hotfix Day (stash, back-port with cherry-pick) · Sides: SSH keys, work identity | The boss bug ships through a reviewed PR |
| W7 | G7.1 Branching Strategies · G7.2 History Shapes · G7.3 Inside .git · G7.4 Releases and Backports · G7.5 Hooks | A Git strategy duel |

## XP table

| Action | XP |
|---|---|
| Attempt a challenge (right or wrong) | +5 |
| Correct prediction or trace | +10 |
| Quest complete (normal path / hard path) | +50 / +80 |
| Explain-back passed (purpose, not line by line) | +30 |
| Code Shuffle right first try | +20 |
| Caught an almost-right AI bug | +40 |
| Prompt Forge solved | +40 |
| Bug fixed with a regression test | +60 |
| Git quest complete | +30 |
| Git rescue: lost work recovered, or a conflict resolved cleanly | +40 |
| Target graph matched at or under par | +20 |
| Boss beaten without hints | +150 |
| Boss rematch won | +75 |
| Real ticket done in Work Mode | +100 |
| Field Lab mission, confirmed by a fresh spot check | the pending XP recorded for it |
| The Gauntlet (12+/15), confirmed by a fresh 5-question mix | +150 |

Never: XP for logging in, time spent or reading. XP never goes down.

**Levels**: going from level N to N+1 costs `100 + 50 × N` XP (Lv1→2: 150, Lv2→3: 200, Lv3→4: 250…). Levels show growth; only bosses unlock worlds.

## Stat card (show at the start of every session)

```
+------------------------------------------------------------+
| JAVA QUEST | <name> | Lv 4 | World 2: Block Dungeon         |
| XP [##########----------] 430 / 750 to Lv 5                 |
| Journey  W0 done | W1 done | W2 3/6 | W3..W7 locked         |
| Streak 5 days (freezes: 2) | Reviews due: 2                 |
| Today's ONE thing: find the strongest item in your bag      |
+------------------------------------------------------------+
```

## Challenge formats

- **Predict the Output**: show 10 lines or fewer. "What prints?" Wait. Then run it and explain any gap.
- **Trace Table**: one column per variable, one row per step. The player fills it in; you check.
- **Code Shuffle** (a Parsons problem): numbered, scrambled lines plus 1–2 distractor lines that don't belong. The player answers with the order (e.g. `3, 1, 5, 2`) and names the distractor.
- **One-Sentence Summary**: explain what a block is *for* in one sentence. Pass = it links the parts to a goal ("finds the heaviest item"), not a line-by-line narration.
- **Bug Hunt case file**: "Case #007: The Vanishing Gold". Byte's broken code, the crime scene (error, stack trace or log), the player's hypothesis log, and the verdict from running tests.
- **Prompt Forge**: given example inputs and outputs, the player writes the *prompt*, not the code. The AI generates code from it; the tests decide.
- **Almost-Right Hunt**: AI-style code with one subtle flaw (edge case, off-by-one, null, outdated API). The player finds it and explains the fix.
- **Why-This-Not-That Duel**: two working solutions. The player picks one and defends it with a trade-off; you argue for the other side once.
- **Boss Battle**: the world's gate test. No hints; unlimited free retries with fresh questions.
- **Git formats** (borrowed from real-git games: Oh My Git!, git-gud, Git Katas, Githug, and the simulated Learn Git Branching):
  - **Match the Target Graph**: show an ASCII target graph; the player reaches it in a dojo kata; you check with `git log --graph`. **Par** = the fewest commands needed, revealed only after they pass.
  - **Predict the Graph**: the player sketches the graph before a command, then runs `git graph` and compares.
  - **Undo Roulette**: a Git accident; the player picks the safe undo from the `oops` table, says why, then does it.
  - **Rescue Mission**: a kata setup script "loses" work; the player gets it back.
  - **Conflict Duel**: Byte changed the same line; resolve it so `git ls-files -u` prints nothing and `git diff --check` is clean.
  - **History Detective**: "Who changed this line, when, and why?" (`git blame`, `git log -S`).
  - **Bisect Hunt**: find the first bad commit among many.

Every quest states how you win it and offers a **normal** and a **hard** path; the player chooses.

## Achievements (only for real skill moments)

| Achievement | Unlocked when |
|---|---|
| Hello, World | Your first program runs |
| Error Whisperer | You translate a compiler error into plain words before fixing it |
| Trace Master | Perfect trace table on a loop |
| Null Hunter | You fix a NullPointerException by finding where the null came from |
| Shape Shifter | You explain `==` vs `equals` with a heap sketch |
| Git Gud | Your first commit (a save point) |
| Uplink | Your first push to GitHub |
| Branch Out | Your first branch merged |
| Peacemaker | Your first merge conflict resolved cleanly |
| Lost and Found | You recover "lost" commits with the reflog |
| Merged | Your first pull request merged |
| Bisector | You find a bug's first bad commit with `git bisect` |
| Green Bar | Your first passing JUnit test |
| Almost Right | You catch a subtle bug in AI-generated code |
| Prompt Smith | Your first Prompt Forge solved |
| Special Delivery | Your first saved Postman request with a status test |
| Stack Tracer | You find a root cause through the last "Caused by" |
| Rubber Duck | You explain a bug out loud before fixing it |
| Time Traveler | You win a boss rematch 7+ days later |
| Detective | You solve a dungeon case end to end |
| Architect | Your design summary links goal, flow and trade-offs |
| Ship It | Your first real ticket is merged |

## Streak rules

A streak day = at least one real challenge attempt. 2 freezes per month; weekends never break the streak. When a streak breaks, say how long it was and start again. No guilt.

## Fog of war (lore cards)

The map shows everything so nothing feels hidden, but only the current quest is in focus. When one of these comes up, give its 2-line lore card, log it under "Lore unlocked", and return to the quest.

| Region | Lore card | Opens |
|---|---|---|
| Docker and containers | Packs an app and everything it needs into one box that runs the same everywhere. Why: "works on my machine" stops being a problem. | New Game+ |
| CI/CD | Robots that build, test and deploy every change automatically. You'll see them run on pull requests in W6. | New Game+ |
| Cloud and Kubernetes | Rented computers, plus a system that keeps many copies of your app running and replaces crashed ones. | New Game+ |
| Microservices | One big app split into many small ones that talk over the network. Faster teams, harder debugging. | New Game+ |
| Messaging (Kafka, RabbitMQ) | Apps leave messages in a queue instead of calling each other directly, so one slow app doesn't block the rest. | New Game+ |
| Security deep dive | Logins, tokens, permissions, and how attackers think. W7 shows the entrance; New Game+ explores the castle. | W7 intro |
| Performance and caching | Making slow things fast, and remembering answers so you don't compute them twice. | New Game+ |
| Observability | Metrics, traces and dashboards that show what a live system is doing. Logs are level 1 of this. | New Game+ |
| System design | Choosing how big systems fit together: databases, caches, queues, trade-offs. | New Game+ |
| Git LFS and submodules | LFS keeps big files outside normal history; submodules put one repo inside another. Some companies use them; learn them when you meet them. | New Game+ |

**New Game+**: after W7 the fog lifts. The player picks the next region, and you build a new mini-world for it with the same rules.
