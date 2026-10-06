# Sources: the research behind Java Quest

For the `why?` command: name the rule, give one line of evidence, and share the link. Be honest about strength: a meta-analysis is not a blog post (see section 9).

## 1. How we explain

| Rule | Evidence | Link |
|---|---|---|
| Hook first; the concept is the payload | Mark Rober: start with a remarkable goal and teach the science "without realizing it" ("hiding the vegetables") | https://www.ted.com/podcasts/how-mark-rober-hides-science-vegetables-in-viral-videos-transcript |
| Failing is free | Rober's Super Mario Effect: about 68% succeeded with no failure penalty vs 52% with one; about 2.5× more attempts | https://www.ted.com/talks/mark_rober_the_super_mario_effect_tricking_your_brain_into_learning_more/transcript |
| Predict before reveal | Curiosity comes from noticing a gap in what you know (Loewenstein 1994); higher curiosity → better recall of answers 1–2 weeks later (Kang et al. 2009) | https://psycnet.apa.org/doi/10.1037/0033-2909.116.1.75 · https://pubmed.ncbi.nlm.nih.gov/19619181/ |
| Never "obviously"; check with explain-back | The curse of knowledge: experts' abstract words leave novices hearing "only opaque phrases" (Heath & Heath 2006) | https://hbr.org/2006/12/the-curse-of-knowledge |
| Explain simply, find the gaps | The Feynman technique | https://subjectguides.york.ac.uk/study-revision/feynman-technique |
| Analogies with stated limits; box → label for variables | Hermans et al. 2018, 496 novices: the "label" metaphor beat "box" on the "a variable holds many values" misconception | https://research.ou.nl/en/publications/thinking-out-of-the-box-comparing-metaphors-for-variables-in-prog/ |
| Concrete → diagram → Java → Spring | Concreteness fading review (Fyfe et al. 2014) | https://eric.ed.gov/?id=EJ1036777 |
| Short chunks, "you", diagram next to code | Mayer's multimedia principles (2017 review: segmenting, personalization, spatial contiguity, coherence); "the" → "your" improved transfer (Mayer et al. 2004) | https://doi.org/10.1111/jcal.12197 · https://psycnet.apa.org/doi/10.1037/0022-0663.96.2.389 |
| Make the player feel capable; keep sub-skills tiny | Kathy Sierra, *Badass* (book report) | https://mtlynch.io/book-reports/badass/ |
| Beginners welcome; "What is working? What is not working?" | CS50 syllabus and Lecture 0 | https://cs50.harvard.edu/x/syllabus/ · https://cs50.harvard.edu/x/notes/0/ |
| Think aloud, show wrong turns | Cognitive apprenticeship: make expert thinking visible (Collins, Brown & Holum 1991); Shiffman "debugs on camera" | https://www.aft.org/ae/winter1991/collins_brown_holum · https://screenwiseapp.com/media/the-coding-train-youtube |
| Treat confusion as normal; one-panel diagrams | Julia Evans | https://www.computinghistory.org.uk/det/76804/Julia-Evans/ |

## 2. The ladder, and what "good enough" means

| Rule | Evidence | Link |
|---|---|---|
| Atoms → blocks → relations → macro | The Block Model (Schulte 2008), textbook summary | https://textbooks.cs.ksu.edu/tlcs/4-designing-cs-lessons/06-the-block-model/ |
| Judge the level by tracing accuracy | Neo-Piagetian stages of novice programmers (Lister; Teague) | https://www.ppig.org/papers/2014-ppig-25th-lister/ · https://eprints.qut.edu.au/86690/ · https://textbooks.cs.ksu.edu/cis400/a-learning-programming/06-developmental-epistemology/index.html |
| Tracing gates explaining; explaining gates writing | Lopez et al. 2008; Venables et al. 2009; "students who cannot trace code usually cannot explain code" | https://opus.lib.uts.edu.au/handle/10453/10806 · https://opus.lib.uts.edu.au/handle/10453/11384 · https://eprints.qut.edu.au/27653/ |
| One-sentence (relational) summaries = pass | Murphy et al. 2012: explaining correlates strongly with writing; better programmers describe how the parts relate | https://opus.lib.uts.edu.au/handle/10453/22969 |
| Bosses are mastery gates | Kulik et al. 1990: mastery programmes improved exam performance across 108 evaluations | https://eric.ed.gov/?q=%22Effectiveness+of+Mastery+Learning+Programs%22 |
| Quiz, don't re-read; spaced reviews | Dunlosky et al. 2013: only practice testing and distributed practice rated high utility | https://scholars.duke.edu/publication/954654 |
| Code Shuffles | Ericson et al.: Parsons problems took less time than fixing or writing the same code, with similar learning | https://www.academia.edu/59279491/Solving_parsons_problems_versus_fixing_and_writing_code |
| Subgoal labels | Morrison et al. 2015 (mixed results for given vs self-written labels) | https://digitalcommons.unomaha.edu/compsicfacproc/61/ |
| Predict → Run → Investigate → Modify → Make | PRIMM: 493 students, higher post-test scores than a control group (Sentance et al. 2019) | https://eric.ed.gov/?id=EJ1217966 |
| Memory sketches + a visualiser | Sorva 2012, visual program simulation | https://research.aalto.fi/en/publications/visual-program-simulation-in-introductory-programming-education/ · https://cscircles.cemc.uwaterloo.ca/java_visualize/ |
| Misconception probes | Kaczmarczyk et al. 2010; Java-specific errors (Hristova 2003; Chen 2012) | https://www.academia.edu/72356639/Identifying_student_misconceptions_of_programming · https://www.academia.edu/92622606/Identifying_and_correcting_Java_programming_errors_for_introductory_computer_science_students |
| Fade support by performance | The expertise reversal effect (Kalyuga et al. 2003) | https://www.academia.edu/4708038/The_Expertise_Reversal_Effect |
| Try first, then get taught (bosses, bug hunts) | Productive failure meta-analysis: 53 studies, g = 0.36 (Sinha & Kapur 2021) | https://eric.ed.gov/?id=EJ1308129 |
| Spring learning order | Official quickstart and REST guide; roadmap.sh | https://spring.io/quickstart · https://spring.io/guides/gs/rest-service · https://roadmap.sh/java · https://roadmap.sh/spring-boot |

## 3. Game design

| Rule | Evidence | Link |
|---|---|---|
| Gamify, but story and challenge matter most | Sailer & Homner 2020 meta-analysis: cognitive g = .49, motivational g = .36, behavioural g = .25; game fiction helped | https://doi.org/10.1007/s10648-019-09498-w |
| Effects depend on context and people | Hamari et al. 2014 | https://doi.org/10.1109/HICSS.2014.377 |
| Progress bars → competence; story and companion → relatedness | Sailer et al. 2017 (experiment) | https://doi.org/10.1016/j.chb.2016.12.033 |
| Puzzles in real typed code | Zhan et al. 2022 meta-analysis of gamified programming (21 studies) | https://doi.org/10.1016/j.caeai.2022.100096 |
| Competence, autonomy, relatedness | Self-determination theory (Ryan & Deci 2000) | https://pubmed.ncbi.nlm.nih.gov/11392867/ |
| No XP for just showing up; praise the skill | 128 studies: expected rewards for taking part or finishing lowered intrinsic motivation; informative positive feedback raised it (Deci, Koestner & Ryan 1999) | https://pubmed.ncbi.nlm.nih.gov/10589297/ |
| Challenge first; points are only the scoreboard | Octalysis ("a badge or trophy without a challenge is not meaningful"); Robertson on "pointsification" | https://medium.com/@yukaichou/the-octalysis-framework-for-gamification-behavioral-design-fe381150f0c1 · https://web.archive.org/web/2010/http://www.hideandseek.net/2010/10/06/cant-play-wont-play/ |
| Byte takes the blame | Gidget: a robot that blamed itself → novices completed more levels (Lee & Ko 2011) | https://researchwith.njit.edu/en/publications/personifying-programming-tool-feedback-improves-novice-programmer/ |
| Streaks with freezes, no guilt | Duolingo experiments (engagement, not learning) | https://blog.duolingo.com/how-duolingo-streak-builds-habit/ · https://blog.duolingo.com/improving-the-streak/ |
| Normal and hard paths | Flow needs challenge matched to skill; Jenova Chen: let players choose difficulty through play | https://en.wikipedia.org/wiki/Flow_(psychology) · https://web.archive.org/web/2020/http://www.jenovachen.com/flowingames/designfig.htm |
| Harder = more XP; no leaderboards | Codewars rank progress; Advent of Code removed its global leaderboard as "one of the largest sources of stress" | https://docs.codewars.com/gamification/ranks/ · https://adventofcode.com/2024/about |
| Compiler and tests decide; case files | SQL Murder Mystery, Oh My Git!, Robocode | https://mystery.knightlab.com/ · https://ohmygit.org/ · https://github.com/robo-code/robocode |
| No "learning styles" | Pashler et al. 2008: virtually no evidence | https://doi.org/10.1111/j.1539-6053.2009.01038.x |

## 4. AI pairing

| Rule | Evidence | Link |
|---|---|---|
| Ask why; never let the AI debug for you | Anthropic 2026 trial (52 developers): AI group 50% vs 67% on the quiz; those who delegated everything under 40%, those who questioned the code 65%+ | https://www.anthropic.com/research/AI-assistance-coding-skills |
| Hints, not answers | Bastani et al. 2025 (PNAS): plain GPT-4 → 17% lower exam scores; a hint-based tutor avoided the drop | https://pmc.ncbi.nlm.nih.gov/articles/PMC12232635/ |
| Guide, don't complete | CS50's AI duck (Liu et al. 2024) | https://doi.org/10.1145/3626252.3630938 · https://cs50.harvard.edu/x/honesty/ |
| Plan first; check yourself without AI | Prather et al. 2024: an "illusion of competence" in struggling novices | https://arxiv.org/abs/2405.17739 |
| Touch the code; pseudo-code + annotations | Kazemitabaar et al. 2023; CodeAid 2024 | https://arxiv.org/abs/2302.07427 · https://arxiv.org/abs/2401.11314 |
| Prompt Forge | Denny et al. 2024, Prompt Problems | https://arxiv.org/abs/2311.05943 |
| Feeling fast isn't evidence | METR 2025: 19% slower while believing they were 20% faster | https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/ |
| Almost-Right Hunts | Stack Overflow 2025: 84% use AI; 46% distrust it; 66% say "almost right, but not quite" | https://survey.stackoverflow.co/2025/ai |
| Review every line; see it run | Addy Osmani (the 70% problem); Simon Willison | https://web.archive.org/web/2025/https://addyo.substack.com/p/the-70-problem-hard-truths-about · https://web.archive.org/web/2025/https://simonwillison.net/2025/Mar/11/using-llms-for-code/ · https://web.archive.org/web/2025/https://simonwillison.net/2025/Mar/19/vibe-coding/ |
| 4-part prompt; plan mode; verify | Codex prompting guide; Claude Code best practices; AGENTS.md | https://learn.chatgpt.com/docs/prompting · https://code.claude.com/docs/en/best-practices · https://agents.md/ |

## 5. Career context (Malaysia)

| Fact | Link |
|---|---|
| Work Trend Index 2024 Malaysia: 84% of knowledge workers use AI; 62% of leaders won't hire without AI skills; 65% prefer a less experienced candidate who has them; 83% of AI users bring their own tools | https://news.microsoft.com/en-my/2024/06/06/microsoft-and-linkedin-release-the-2024-work-trend-index-on-the-state-of-ai-at-work-in-malaysia/ |
| Work Trend Index 2025 Malaysia: 86% of leaders expect to use AI agents to expand capacity within 12–18 months | https://news.microsoft.com/en-my/2025/05/08/microsofts-2025-work-trend-index-malaysian-workforce-and-leadership-align-on-intelligent-agent-integration/ |
| National AI Office launched 12 Dec 2024 | https://www.mydigital.gov.my/initiatives/the-national-ai-office-naio/ · https://ai.gov.my/ |
| TalentCorp: about 620,000 workers in 10 sectors, ICT included, significantly affected within 3–5 years | https://www.talentcorp.com.my/impact-study/ · https://www.mymahir.my/publication/1/impact-study-of-ai-digital-and-green-economy-on-the-malaysian-workforce |

## 6. Real work, debugging and getting unstuck

| Rule | Evidence | Link |
|---|---|---|
| Model, coach, fade, reflect | Cognitive apprenticeship | https://www.aft.org/ae/winter1991/collins_brown_holum |
| Real tasks, from the edge inward | Situated learning (Lave & Wenger); GitHub's "good first issue" label | https://www.cambridge.org/highereducation/books/situated-learning/6915ABD21C8E4619F750A4D4ACA616CD · https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/encouraging-helpful-contributions-to-your-project-with-labels |
| Newcomers need a way to start, and people | Steinmacher et al.: 15 newcomer barriers; Dagenais et al. 2010; mentoring (Fagerholm et al. 2014) | https://experts.nau.edu/en/publications/a-systematic-literature-review-on-the-barriers-faced-by-newcomers/ · https://research.ibm.com/publications/moving-into-a-new-software-project-landscape · https://research.aalto.fi/en/publications/the-role-of-mentoring-and-project-characteristics-for-onboarding- |
| Teach debugging as a process | Michaeli & Romeike 2019 | https://portal.fis.tum.de/en/publications/improving-debugging-skills-in-the-classroom-the-effects-of-teachi/ |
| Trace with a variable table | Xie et al. 2018: +15% on tracing | https://par.nsf.gov/biblio/10107747-explicit-strategy-scaffold-novice-program-tracing |
| Hypothesis → prediction → experiment; fix only when explained | Zeller, *The Debugging Book* | https://www.debuggingbook.org/html/Intro_Debugging.html |
| Error messages are hard for novices | Never Work in Theory summary | https://neverworkintheory.org/2021/09/02/compiler-error-messages-considered-unhelpful.html |
| Stack traces and "Caused by" | Oracle Java 21 `Throwable` docs | https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/lang/Throwable.html |
| Understanding code is most of the job | Xia et al. 2018: about 58% of developers' time | https://research.monash.edu/en/publications/measuring-program-comprehension-a-large-scale-field-study-with-pr/ |
| Struggle is "common and temporary" | Walton & Cohen 2011 belonging intervention; growth-mindset effects were weak overall (Sisk et al. 2018), so no mindset slogans | https://doi.org/10.1126/science.1198364 · https://doi.org/10.1177/0956797617739704 |
| Stories and acceptance criteria | Atlassian | https://www.atlassian.com/agile/project-management/user-stories · https://www.atlassian.com/work-management/project-management/acceptance-criteria |
| Bug reports: steps to reproduce first | Bugzilla bug-writing guidelines | https://bugzilla.mozilla.org/page.cgi?id=bug-writing.html |
| Postman requests + status tests | Postman docs | https://learning.postman.com/docs/getting-started/first-steps/sending-the-first-request/ |
| 4xx vs 5xx | MDN HTTP status codes | https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status |

## 7. Git and GitHub

| Rule | Evidence | Link |
|---|---|---|
| Git woven in feature by feature, not saved for the end | Haaranen & Lehtinen 2015: "incrementally present features of Git and incorporate them into the course workflow" | https://doi.org/10.1145/2729094.2742608 |
| Graph picture from the first commit; SSH later | Wagner & Thurner 2025: learners feel "overwhelmed by the plethora of Git's detailed commands and options"; start from branches and separate concepts from commands | https://eric.ed.gov/?id=EJ1464208 |
| The staging area and "edits follow you when you switch" are Git's design traps, not the player's fault | De Rosso & Jackson 2013 ("Git puzzles even experienced developers") and 2016 (concept "misfits") | https://dspace.mit.edu/handle/1721.1/105233 · https://2016.splashcon.org/details/splash-2016-oopsla/34/Purposes-Concepts-Misfits-and-a-Redesign-of-Git |
| The four pictures | Pro Git: snapshots; "modified, staged, and committed"; a branch is "a lightweight movable pointer"; remote-tracking branches are "bookmarks" | https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F · https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell · https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches |
| The data model first, lightly | MIT Missing Semester: learning Git top-down "can lead to a lot of confusion" | https://missing.csail.mit.edu/2020/version-control/ |
| Word twins | Julia Evans, "Confusing git terminology" | https://jvns.ca/blog/2023/11/01/confusing-git-terminology/ |
| Terminal first; a GUI for diffs and conflicts | Pro Git: "the command line is the only place you can run all Git commands"; Software Carpentry teaches commands so learners know what runs; VS Code: "The editor and command-line Git use the same repository" | https://git-scm.com/book/en/v2/Getting-Started-The-Command-Line · https://swcarpentry.github.io/git-novice/ · https://code.visualstudio.com/docs/sourcecontrol/overview |
| Trap quests (push before pull, detached HEAD, forgetting `git add` after a conflict) | Software Carpentry instructor notes: "The most common mistake is that learners push before pulling" | https://swcarpentry.github.io/git-novice/instructor/instructor-notes.html |
| Most practice on undo and syncing | Stack Overflow's top Git questions: undo the last commit (27k votes, 16.8M views), delete a branch, fetch vs pull, undo `git add` | https://stackoverflow.com/questions/927358 |
| Safety colours; commit early | Pro Git "Undoing Things" and "Reset Demystified"; the reflog docs | https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things · https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified · https://git-scm.com/docs/git-reflog |
| The `oops` table | "Oh Shit, Git!?!" (the swear-free version) | https://dangitgit.com/en |
| Teach `switch` and `restore` | Added in Git 2.23 (2019); no longer experimental since Git 2.51 (2025) | https://github.blog/open-source/git/highlights-from-git-2-51/ |
| Target graphs, par, setup + win scripts, verify/reset, a teammate bot | Learn Git Branching, Oh My Git!, git-gud, Githug, Git Katas, Git Exercises, Git-it | https://github.com/pcottle/learnGitBranching · https://ohmygit.org/ · https://github.com/benthayer/git-gud · https://github.com/Gazler/githug · https://github.com/eficode-academy/git-katas · https://github.com/fracz/git-exercises · https://github.com/jlord/git-it-electron |
| Predict the graph, don't just watch it | Naps et al. 2002: a visualisation "is of little educational value unless it engages learners in an active learning activity" | https://doi.org/10.1145/960568.782998 |
| Check the graph, the files AND an explain-back | Git games are barely evaluated; a 2026 study of a collaborative Git platform found mixed performance results | https://doi.org/10.1145/3772318.3791254 |
| GitHub flow first; short-lived branches | GitHub flow docs; Git flow's 2020 note of reflection; DORA on trunk-based development | https://docs.github.com/en/get-started/using-github/github-flow · https://nvie.com/posts/a-successful-git-branching-model/ · https://dora.dev/capabilities/trunk-based-development/ |
| Small PRs; the review checklist | Google engineering practices | https://google.github.io/eng-practices/review/developer/small-cls.html · https://google.github.io/eng-practices/review/reviewer/looking-for.html |
| Commit messages | Chris Beams' 7 rules | https://cbea.ms/git-commit/ |
| The rebase rule | Pro Git "Rebasing" | https://git-scm.com/book/en/v2/Git-Branching-Rebasing |
| cherry-pick, revert, bisect, stash | Git reference docs | https://git-scm.com/docs/git-cherry-pick · https://git-scm.com/docs/git-revert · https://git-scm.com/docs/git-bisect · https://git-scm.com/docs/git-stash |
| Draft PRs, closing keywords, merge methods, required checks | GitHub docs | https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests · https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue · https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/about-merge-methods-on-github · https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches |
| Resolving conflicts in the terminal | GitHub docs | https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line |
| Windows setup and first-time settings | Git for Windows install page; Pro Git first-time setup | https://git-scm.com/install/windows · https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup |
| Two-factor sign-in | GitHub requires 2FA for everyone who contributes code (since 2023) | https://github.blog/news-insights/product-news/raising-the-bar-for-software-security-github-2fa-begins-march-13/ |
| Private commit email | GitHub's noreply address | https://docs.github.com/en/account-and-profile/reference/email-addresses-reference |
| HTTPS + Git Credential Manager first; SSH later | GitHub recommends GitHub CLI or Git Credential Manager for HTTPS; password sign-in for Git ended in August 2021 | https://docs.github.com/en/get-started/git-basics/caching-your-github-credentials-in-git · https://github.blog/security/application-security/token-authentication-requirements-for-git-operations/ |
| An empty repo for the first push | GitHub: "do not initialize the new repository with README, license, or gitignore files" | https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github |
| Secrets: change them first; push protection is a safety net | GitHub docs | https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository · https://docs.github.com/en/code-security/secret-scanning/introduction/about-push-protection |
| `.gitignore` templates | github/gitignore | https://github.com/github/gitignore |
| Git is everywhere | Stack Overflow 2022: 93.87% of developers use Git; 83.57% use it on the command line | https://survey.stackoverflow.co/2022/#version-control |

## 8. Borrowed designs (and what we changed)

| Source | Borrowed | Changed |
|---|---|---|
| Sensei – Junior Mentor (awesome-copilot) | PEAR loop, 4-level hint ladder, stakes switch | tied to power-up levels |
| Demonstrate Understanding (awesome-copilot) | explain-back, one question at a time | used as boss checks |
| Microsoft Study and Learn (awesome-copilot) | ask the level first, short turns | — |
| Bloom | mastery checklist, warm-up question, learning log | the save file is markdown |
| learn-faster-kit | spaced review schedule; plain-text menus in Codex | — |
| Claude Code "Learning" output style | `TODO(human)` hand-offs | `// TODO(you)` scaffolds |
| Chat Reincarnation (llm_games) | teach-the-character quests, stats every turn | the compiler and tests judge, not the LLM |
| Mr. Ranedeer | Socratic mode, /test | dropped "learning styles" (no evidence) |
| Oh My Git! and Git Katas | setup scripts + win conditions for Git levels | local-only katas the player runs |
| Learn Git Branching and git-gud | target graphs and par | checked on real Git, plus an explain-back |

Links: https://github.com/github/awesome-copilot/blob/main/agents/mentoring-juniors.agent.md · https://github.com/github/awesome-copilot/blob/main/agents/demonstrate-understanding.agent.md · https://github.com/github/awesome-copilot/blob/main/agents/microsoft-study-mode.agent.md · https://github.com/Li-Evan/Bloom · https://github.com/cheukyin175/learn-faster-kit · https://code.claude.com/docs/en/output-styles · https://github.com/fladdict/llm_games · https://github.com/JushBJJ/Mr.-Ranedeer-AI-Tutor

## 9. Honesty notes (weaker evidence, used with care)

- Rober's Super Mario Effect is a TEDx talk, not a peer-reviewed study; the method wasn't published, and the numbers come from a transcript.
- The 80–90% mastery threshold comes from a Wikipedia summary; the primary sources were blocked.
- METR's 2026 follow-up leans toward a speedup for AI users, but METR itself calls that data unreliable (selection effects).
- The Wilkes and Kernighan quotes are via Wikiquote; the Ira Glass quote is via a transcript site.
- Duolingo's numbers measure engagement, not learning. Octalysis and "pointsification" are designers' opinions, not experiments.
- Timebox lengths (e.g. "30 minutes before asking a human") are design choices, not research numbers.
- No controlled study compares the command line with GUIs for learning Git, and Git games have almost no formal evaluations. The Git track follows expert practice (Pro Git, Software Carpentry, MIT) plus general learning research (PRIMM, active visualisation).
- Some pages (jvns.ca, nvie.com, Atlassian) were read through web.archive.org copies during research.
