# World 6: The Real Job

**Story**: real jobs almost never start with an empty folder. You join a codebase other people wrote, with a Jira board full of tickets, logs full of noise, and a README that's slightly out of date. This world simulates exactly that, safely.
**Power-up: Commander.** The AI may plan and implement multi-step work with you. You still review every line, run the tests, run git yourself, and explain the change.
**Where this shows up at work**: this IS the work. A field study of professional developers found they spend about 58% of their time understanding existing code (Xia et al. 2018).

## Building the dungeon (do this once, at the start of W6)

1. **The code.** Generate a small Spring Boot app in `dungeon/guild-hall/`:
   - Same Java and Spring Boot versions as PRISM if the player knows them; otherwise Java 21 + the latest Spring Boot.
   - 15–25 files: `Hero`, `Quest` and `Reward` entities with controllers, services and repositories; an H2 database with seed data; a few tests; a Postman collection; a `.gitignore` from the github/gitignore templates.
   - Realistic legacy touches: an outdated README step, one `TODO`, inconsistent naming in one place, a missing test.
   - T2's and T3's bugs are in the code from the start. Write the code WITHOUT T6's bug; the history adds it.
2. **The history.** Write `dungeon/build-history.sh` for the player to run once in Git Bash. Follow the kata rules in `game/playbooks/git.md` (local only, fictional authors with `@guild.example` emails, never touch global config) and back-date commits with `GIT_AUTHOR_DATE` and `GIT_COMMITTER_DATE`:
   - `main`: the code arrives in 3–4 commits by different "teammates" over a few weeks → tag `v1.0` → 5–8 small realistic commits (README fix, a new test, a rename, a log line) made with `sed` or `printf`. One of them quietly introduces T6's bug with a one-line change and an innocent message → tag `v1.1`, the version in production.
   - `release/1.1` starts at `v1.1`: the production line, which only receives fixes.
   - `main` moves on with 2–3 commits for the next release. The last one is Byte's, and it breaks two tests.
   - Byte's unmerged branch `feature/byte-quest-timer`: 2–3 commits with one planted problem, for a code review.
3. **The spoilers.** Write the answers in `dungeon/GM-SPOILERS.md`, outside the repo so it's never pushed. Tell the player: "No peeking. Opening the spoilers counts as using every hint."
4. **The team setup (the player does this)**: create a new **private** GitHub repo `guild-hall`; push all branches and tags (`git push -u origin --all`, `git push origin --tags`); keep `main` as the default branch, so "Closes #N" in a PR closes its issue; create GitHub Issues T1–T6 from your ticket texts. Team rule from now on: nothing reaches `main` or `release/1.1` except through a pull request.

Ticket board (write each one Jira-style: title, user story, acceptance criteria, and steps to reproduce for bugs):

| Ticket | Type | Target branch | Summary |
|---|---|---|---|
| T1 | Onboarding | — | Run the app, send each Postman request, draw the request flow for `GET /quests/{id}` |
| T2 | Bug (small) | `main` | Completing a quest pays out one reward too few (an off-by-one) |
| T3 | Bug | `main` | Viewing a hero with no guild crashes with a 500 (a NullPointerException) |
| T4 | Minor feature | `main` | Filter quests by difficulty: `GET /quests?difficulty=HARD` |
| T5 | Big feature | `main` | Parties: heroes team up to take a quest together. Needs design, an API and tests |
| T6 | Incident | `main`, then back-ported to `release/1.1` | "The rewards page sometimes returns 500" in production (`v1.1`). Only the logs know why |

## Missions (Java and Git, together)

| ID | Mission | Skills | Git quests |
|---|---|---|---|
| M6.1 | New Hire Day (T1) | Code Reading Club: skim the structure → pick one endpoint → trace it from controller to database → one-line job per class. Turn acceptance criteria into a checklist | **G6.1 Red Build on Day One**: tests fail on `main`. Find Byte's commit (`git log`, `git show`) and undo it the shared-branch way: `git revert <hash>` on a branch, then a PR. **G6.2 History Detective**: `git graph`, `git shortlog -sn`, `git blame -L`, `git log -S`, `git log -p -- <file>`: who changed this, when, and why? |
| M6.2 | First Bugs (T2, T3) | Reproduce first (Postman or a failing test) → read the stack trace (last "Caused by", then the first line in our code) → hypothesis log → fix → regression test | **G6.3 Ticket Branches**: `git fetch`, `git switch -c bugfix/T2-reward-payout origin/main`; commit the failing test, then the fix; stay current with `git fetch` + `git merge origin/main`; push; PR into `main` with "Closes #2" |
| M6.3 | Minor Feature (T4) | Plan in steps, small commits, Postman tests, the PR description | **G6.4 Review Round-trip**: open the PR early as a draft, and mark it ready when done. You review like a senior (`git diff origin/main...feature/T4-difficulty-filter` + the checklist in `game/playbooks/git.md`) and give comments; the player pushes fix commits to the same branch (the PR updates itself), replies to each comment, merges with **Squash and merge**, then cleans up (`git branch -D` after a squash merge, `git fetch --prune`) |
| M6.4 | Incident (T6) | Logs: find the time → the request → the stack trace. 4xx means check the request; 5xx means check the server. Write a mini post-mortem: what, why, fix, prevention | **G6.5 Bisect Hunt**: `git bisect start`, `git bisect bad v1.1`, `git bisect good v1.0`, test each stop, `git bisect reset` (hard path: `git bisect run`). **G6.6 Hotfix Day**: pocket the T5 work (`git stash push -u`, or a WIP commit); fix on `hotfix/T6-rewards-500` from `origin/main`; PR into `main` with "Closes #6"; then back-port it to production: `git switch -c backport/T6 origin/release/1.1`, `git cherry-pick -x <fix-hash>`, PR into `release/1.1`, then tag `v1.1.1` and push the tag |
| M6.5 | Big Feature (T5) | Design first (endpoints, data, edge cases), then build in slices with tests. Review it as if you were the senior. Show the plan to your real mentor | Several small PRs instead of one giant one; merge `origin/main` into the branch at least daily (short-lived branches); review Byte's branch with `git diff origin/main...origin/feature/byte-quest-timer` and the review checklist in `game/playbooks/git.md` |

**Side quests** (before PRISM Work Mode):
- **Keys to the Kingdom**: SSH keys: `ssh-keygen -t ed25519 -C "<email>"`, the Windows ssh-agent, the public key added to GitHub, then `ssh -T git@github.com`. Some teams use SSH remote URLs (`git@github.com:…`) instead of HTTPS; ask the mentor which one the team uses.
- **Two Identities**: keep work repos in their own folder with the work email, using `includeIf` (`game/playbooks/git.md`, last section). Personal email on personal code; work email on work code.

## Boss: The Case File

A fresh bug you plant in the dungeon (not T1–T6). A small setup script adds a teammate's branch with a few innocent commits plus the bad one. The player pushes it and merges it through a PR with **Create a merge commit** (so bisect can see each commit), as if a teammate's approved PR just landed. Then your bug report arrives. The player files it as an issue and works it end to end: reproduce, find where it came from (`git bisect` or `git log -S`), hypothesis log, fix, regression test, explain every changed line, then ship it through a reviewed PR: a ticket branch from `main`, a clear description with "Closes #N", review fixes pushed to the same branch, merged with the repo's merge method.
No hints. Achievements **Detective** and, if bisect was used, **Bisector**.

Winning unlocks W7 Architect's Tower. **PRISM Work Mode unlocks too**, once the player's lead agrees; then set "PRISM unlocked: yes" in the save file. At work, the first PR follows the team's own rules (branch names, PR template, reviewers, required checks) with the mentor watching.
