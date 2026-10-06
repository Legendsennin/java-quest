# World 7: Architect's Tower

**Story**: you can fix bugs and ship features. Now you learn to see the whole castle: why it was built this way, what's hidden inside the walls, and how to make choices that still look good in a year.
**Power-up: Commander.**
**Where this shows up at work**: senior engineers get asked "why?" all day. This world trains the answers.

## Quests

| ID | Quest | Concepts |
|---|---|---|
| Q7.1 | Reading From the Top | Read a codebase top-down: entry points, packages, configuration, the flow of one feature. The 5-sentence summary: goal, flow, decision, alternative, consequence |
| Q7.2 | Patterns in the Wild | Spot patterns in real Spring code: dependency injection, repository, strategy, template method, builder, factory, facade |
| Q7.3 | Behind the Curtain | How Spring works inside: beans, proxies, and why `@Transactional` has no effect when a method calls another method in the same class |
| Q7.4 | The Vault Deep Dive | Transactions and rollback, lazy vs eager loading, the N+1 query problem |
| Q7.5 | The Gatekeepers | The Spring Security filter chain, authentication vs authorisation, profiles and secrets |
| Q7.6 | The Test Pyramid | Unit vs slice vs integration tests: what each is for, cost vs confidence |
| Q7.7 | Design Duels | Trade-offs: where validation lives, entity vs DTO, synchronous vs asynchronous, when *not* to add a pattern |

## Git quests: history as design

| ID | When | Quest |
|---|---|---|
| G7.1 | with Q7.1 | **Branching Strategies**: GitHub flow vs Git flow (its author's 2020 note says continuously delivered apps should use something simpler) vs trunk-based development. DORA's research favours short-lived branches merged into trunk at least daily. Which fits an app that ships continuously, and which fits software with numbered releases? |
| G7.2 | with Q7.7 | **History Shapes**: GitHub's three merge methods: merge commit, squash and merge, rebase and merge. What does each cost later, when you need `blame`, `revert` or `bisect`? (Duel) |
| G7.3 | with Q7.3 | **Inside .git**: prove a commit is a snapshot: `git cat-file -p HEAD`, `git cat-file -p 'HEAD^{tree}'`, `cat .git/HEAD`, `ls .git/refs/heads` |
| G7.4 | with Q7.6 | **Releases and Backports**: tags and SemVer, release branches, `cherry-pick -x` and its trap: two copies of one change that can conflict later |
| G7.5 | any time | **Hooks**: `pre-commit` and `commit-msg` hooks (for example, a formatter or a commit-message checker); why `--no-verify` is a red flag in review |

## Challenge focus

- **5-sentence summaries** of unfamiliar features, confirmed by tracing a real request.
- **Duels** with no single right answer, only trade-offs defended well.
- **Almost-Right Hunts** on AI code that works but is badly designed.

## Boss: The Architect

1. A 5-sentence summary of an unfamiliar feature (in the dungeon or PRISM), confirmed by a trace.
2. Win a design duel: defend a choice against the strongest counter-argument. The duel may be about a Git strategy: pick a branching model and merge method for a described team, and defend it.

Achievement **Architect**. Then **New Game+**: the fog lifts (see `game/world-map.md`).
