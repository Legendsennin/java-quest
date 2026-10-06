# Playbook: Git and GitHub

Git is the save system for code; GitHub is a website that keeps copies of Git repos online and adds teamwork tools. In the last Stack Overflow survey that asked (2022), about 94% of developers used Git and about 84% used it from the command line. Here Git is taught in the terminal, one piece at a time, woven into every world (quests `G<world>.<n>`).

## Rules for the Game Master

1. **The player types every Git command**, in Git Bash, in a second terminal next to Codex. Never run Git commands that change anything (Codex's sandbox also keeps `.git` read-only).
2. **Check with read-only commands only**: `git --no-optional-locks status -sb`, `git log --oneline --graph --all -n 20`, `git show --stat <ref>`, `git diff`, `git diff --cached`, `git for-each-ref`, `git rev-parse`, `git ls-files -u`, `git diff --check`, `git reflog -n 10`, `git config --get <key>`. Point at a repo with `git -C <path>`. (`--no-optional-locks` stops `status` from writing, per the Git docs.) You have no network: to check a push, ask the player to run `git fetch`, then read `git status -sb`.
3. **Predict → run → compare → explain** for every new command: "What will `git status` say now?" They run it; you compare.
4. **Show the map** after every command that changes history. The player predicts or sketches the graph first, then runs `git graph` (alias from W0). Watching a visual teaches little unless the learner actively predicts or builds it (Naps et al. 2002).
5. **One new Git word at a time, with its plain twin** (table below).
6. **Before any RED command**, the player runs `git status` and makes a backup: `git branch backup/<name>`.
7. **Git XP needs three things**: the right graph, the right file contents, and an explain-back. A structure-only check can pass a wrong answer.
8. **Git and GitHub are different things.** Say it early, say it often.
9. Teach `git switch` and `git restore` (stable since Git 2.51). Show `git checkout` once, as the older form found in old answers.

## The four pictures (teach in this order; reuse in every hint)

```
1. SNAPSHOTS     (A) <- (B) <- (C)               each commit = a photo of the whole project + an arrow to its parent

2. THREE AREAS   workbench  --git add-->  loading dock  --git commit-->  vault
                 (your files)             (staging area)                 (.git history)

3. LABELS        (A) <- (B) <- (C)  <- main  <- HEAD ("you are here")
                         \
                          (D)       <- feature/spells                    a branch is a sticky label on one commit

4. REMOTES       your vault  --push-->  GitHub ("origin")  --fetch-->  your postcard: origin/main
```

- Pro Git: Git stores "a series of snapshots"; "modified, staged, and committed" is "the main thing to remember"; a branch is "a lightweight movable pointer"; remote-tracking branches are like "bookmarks".
- Uncommitted edits belong to no snapshot and follow you when you switch branches. It's a known trap in Git's design (De Rosso & Jackson), not the player's fault.

## Word twins (unlock each one only when first needed)

| Git word | Plain twin |
|---|---|
| working tree | your files, right now |
| staging area / index / "cached" (three names, one thing) | the loading dock |
| commit | a save point (a snapshot) |
| hash (`a1b2c3d`) | the save point's ID |
| branch | a sticky label that moves forward with each new commit |
| HEAD | the "you are here" pin |
| detached HEAD | spectator mode: visiting a save point, not standing on a label |
| remote / `origin` | a nickname for the GitHub copy's address |
| `origin/main` | a postcard: what GitHub looked like when you last checked |
| fetch | check the mail (update the postcards; touch nothing else) |
| pull | check the mail, then update your branch |
| push | send your new save points to GitHub |
| merge | join two lines of history |
| conflict | a question Git can't answer alone. Not a crash |
| reflog | the flight recorder: everywhere HEAD has been (on this PC only) |
| stash | a pocket for unfinished work |
| tag | a permanent label for a release (`v1.0.0`) |
| pull request (PR) | "please review and merge my branch": a GitHub feature, not a Git command |

## Safety colours

| Colour | Commands | Why |
|---|---|---|
| GREEN: safe | `status`, `log`, `diff`, `show`, `add`, `commit`, `switch`, `branch <name>`, `fetch`, `push`, `merge`, `revert`, `stash push`, `tag` | read-only, or only adds history |
| YELLOW: rewrites your own history | `commit --amend`, `reset --soft` / `--mixed`, `rebase`, `stash pop` / `drop` | fine only for commits never pushed; a dropped stash is hard to get back |
| RED: can destroy work | `restore <file>`, `reset --hard`, `clean -fd`, `branch -D`, `push --force` | uncommitted work deleted this way is usually gone for good; a forced push can erase teammates' work |

Pro Git: "Anything that is committed in Git can almost always be recovered… anything you lose that was never committed is likely never to be seen again." So: commit early and often.
If a force push is ever truly needed on your OWN branch: `git push --force-with-lease`. Never plain `--force`, never on a shared branch.

## The `oops` table

Ask what happened, run read-only checks, then walk through the fix one command at a time.

| Situation | Safe move |
|---|---|
| Staged the wrong file | `git restore --staged <file>` |
| Want a file back as it was at the last commit (your edits will be lost) | `git restore <file>` (RED) |
| Typo in the last commit message, not pushed | `git commit --amend` |
| Forgot a file in the last commit, not pushed | `git add <file>`, then `git commit --amend --no-edit` |
| Undo the last commit but keep the changes, not pushed | `git reset --soft HEAD~1` |
| Committed to `main` instead of a branch, not pushed | `git branch feature/x`, then `git reset --hard HEAD~1`, then `git switch feature/x` |
| A bad commit is already pushed | `git revert <hash>` (a new commit that undoes it) |
| Lost commits after a reset | `git reflog`, then `git branch rescue <hash>` |
| Deleted a branch by mistake | `git reflog`, then `git branch <name> <hash>` |
| Made commits in detached HEAD | `git switch -c <new-branch>` before leaving |
| A merge went wrong and isn't committed yet | `git merge --abort` |
| Pushed a secret (password, key, token) | Revoke or change the secret FIRST and tell the mentor. Deleting it in a new commit doesn't remove it from history |

## Commit messages

- Subject: imperative, capitalised, 50 characters or fewer, no full stop. Test: "If applied, this commit will ___."
- Then a blank line and a body (wrapped at 72) explaining **what and why**, not how (Chris Beams' 7 rules).
- Good: `Fix off-by-one in reward payout`. Bad: `fixed stuff`, `wip`, `asdf`.
- One commit = one idea. On your own branch, commit early and often.

## First push/pull troubleshooting

| Message | Cause | Fix |
|---|---|---|
| `Author identity unknown` / `Please tell me who you are` | name or email not set | the W0 `git config --global` commands |
| `src refspec main does not match any` | no commit yet, or the branch isn't called `main` | `git status`; commit first, or `git branch -M main` |
| `remote origin already exists` | `git remote add` ran twice | `git remote -v`, then `git remote set-url origin <url>` |
| `! [rejected] … (fetch first)` or `(non-fast-forward)` | GitHub has commits you don't | `git fetch`, `git merge origin/main`, then `git push`. Never `--force` |
| `fatal: Not possible to fast-forward, aborting.` | both sides have new commits; `pull.ff only` won't guess how to combine them | `git fetch`, then `git merge origin/main`, then `git push` |
| `Need to specify how to reconcile divergent branches` | the same, on a PC without the W0 settings | run the G0.3 settings, then as above |
| `refusing to merge unrelated histories` | the GitHub repo was created with a README | recreate it empty, or `git pull --no-rebase --allow-unrelated-histories origin main` |
| `Support for password authentication was removed` | the account password was typed at a prompt | sign in through the browser window (Git Credential Manager); delete the old GitHub entry in Windows Credential Manager |
| `Permission denied (publickey)` | SSH key missing | use the HTTPS URL, or do the W6 SSH side quest |
| `LF will be replaced by CRLF` | Windows line-ending conversion | information only; safe to ignore |
| `The current branch … has no upstream branch` | first push of a branch without `-u` | `git push -u origin <branch>` |
| `error: failed to push some refs` | only a summary | read the `! [rejected]` and `hint:` lines above it |

## Team flows

**GitHub flow (W4–W5)**: one branch per task → PR → review → merge → delete.
```bash
git switch main && git pull                        # start from a fresh main
git switch -c feature/12-health-endpoint           # one branch per ticket
git add <files> && git commit                      # small commits, good messages
git fetch && git merge origin/main                 # stay current
git push -u origin feature/12-health-endpoint      # backup + PR source
# open the PR on GitHub ("Closes #12"), push review fixes to the same branch, merge
git switch main && git pull                        # after the merge on GitHub
git branch -d feature/12-health-endpoint           # -D if it was squash-merged
git fetch --prune                                  # forget branches deleted on GitHub
```

**Hotfix with stash and cherry-pick (W6)**: fix it on `main` first, then back-port it to the release line.
```bash
git stash push -u -m "WIP T5 parties"              # pocket unfinished work
git switch -c hotfix/T6 origin/main                # fix on main first
git commit -am "Fix 500 when a hero has no rewards"
git push -u origin hotfix/T6                       # PR into main ("Closes #6"), merge
git fetch
git switch -c backport/T6 origin/release/1.1       # the version in production
git cherry-pick -x <fix-hash-on-main>              # -x records where it came from
git push -u origin backport/T6                     # PR into release/1.1, merge, tag v1.1.1
git switch feature/T5-parties && git stash pop     # back to what you were doing
```

**The pull request cycle (from W4, and at work)**
1. Open the PR early as a **draft**: drafts can't be merged, and code owners aren't asked to review yet. Mark it "Ready for review" when it's done.
2. The description says what changed, why, and how it was tested. "Closes #N" closes the issue when the PR merges into the default branch.
3. Reviewers leave comments. Push fix commits to the same branch; the PR updates itself. Reply to every comment.
4. Stay current: `git fetch`, then `git merge origin/main`. Some repos require the branch to be up to date and the checks (tests) to pass before merging.
5. Merge with the repo's method: **merge commit** (keeps every commit), **squash and merge** (one commit on `main`; the branch's separate commits and their authors aren't kept), or **rebase and merge** (replays the commits with new hashes). After a squash merge, start new work on a fresh branch from `main`; carrying on with the old branch brings its old commits and conflicts back.
6. Clean up: delete the branch on GitHub, then `git switch main`, `git pull`, `git branch -d <branch>` (`-D` after a squash merge) and `git fetch --prune`.

At work, the repo's own rules come first: branch names, PR template, required reviewers and checks. Ask the mentor.

## Reviewing a pull request

Google's engineering practices, in order: **design** first (does this change belong here?), then functionality, complexity, tests, naming, comments, style. Prefix optional points with "Nit:". Be kind, explain your reasoning, and say what's good too. Small changes review best: about 100 changed lines is reasonable; 1,000 is usually too big.
Read only the branch's own changes with three dots: `git diff <target>...<branch>`.

## Dojo katas (throwaway practice repos)

For rescue drills, graph puzzles, conflicts and bisect hunts, write a setup script that the player runs. Never create the history yourself.

```bash
# dojo/vanished-commits/setup.sh
# WIN: bring back the two lost commits onto a branch called rescue.
set -e
cd "$(dirname "$0")"
rm -rf exercise && git init -q -b main exercise && cd exercise
save() { git add -A && git -c user.name="Byte" -c user.email="byte@guild.example" commit -q -m "$1"; }
echo "hp = 10" > hero.txt; save "Add hero stats"
echo "mp = 5" >> hero.txt; save "Add mana"
echo "xp = 0" >> hero.txt; save "Add experience"
git reset -q --hard HEAD~2
echo "Kata ready. cd dojo/vanished-commits/exercise"
```

Rules: local only (no network, no pushes); never change global config; fictional authors with `@guild.example` emails; re-running resets the kata. The WIN line at the top is the goal you show the player (Oh My Git! style). Check the result with read-only commands.

## Keep work and personal separate

- Company code, configs, logs and customer data never go into a personal repo, fork, gist or issue, public or private. They stay in the company's own repos.
- Before the first push in any repo, check `git config user.email` and `git remote -v`: right identity, right destination.
- At work, keep work repos in their own folder with a work identity. In `~/.gitconfig`: `[includeIf "gitdir/i:C:/work/"]` with `path = ~/.gitconfig-work`, a file that sets the work email.
