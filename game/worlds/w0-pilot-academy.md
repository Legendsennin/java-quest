# World 0: Pilot Academy

**Story**: every great pilot starts in a simulator. Before you take off into Java, you learn how to fly with an AI co-pilot, and you'll run real Java in your first 10 minutes.
**Cool build**: your first Java lines running live, your own Pilot Rules card, and your save system: Git plus a GitHub account.
**Power-up**: Tutor (the AI explains, quizzes and gives hints; you write the code).

## First Launch (only when the save file has no player name)

1. Welcome in 3 short lines: Java Quest is a game; failing is free; progress saves automatically.
2. Ask, one at a time:
   - "What should I call you? A gamer tag is fine."
   - "Which games do you play most?" (Used for examples and analogies.)
   - "Have you written any code before, in any language?"
3. Setup check: run `java -version` and `git --version`, and open **Git Bash** as the second window. Fix anything missing together, one step at a time.
4. Show the stat card and the `map` once, so the whole journey is visible.
5. Save name, games and coding background under Player and Tutor notes. Start Q0.1.

## Quests

### Q0.1 Boot Sequence (first win within 10 minutes)

- Hook: "In the next 5 minutes you'll give Java its first orders."
- In a second terminal, open `jshell`: Java's live console. You type a line and it answers instantly, like a game's command console.
- Three lines. Predict each result before pressing Enter:
  1. `2 + 3`
  2. `"GG" + " WP"`
  3. `System.out.println("Hello, " + "<name>")`
- `/exit` to leave. Achievement: **Hello, World**.
- One idea to plant: a program is a list of exact instructions. The computer does exactly what you say, not what you mean.

### Q0.2 Pilot or Passenger?

Hook: "Two people use the same AI. One gets hired and gets better every month. The other is stuck the first time the AI is wrong. What's the difference?"

Real data (cite when you use it; links in `game/sources.md`):
- Microsoft & LinkedIn Work Trend Index 2024, Malaysia: 84% of knowledge workers already use AI at work; 62% of leaders wouldn't hire someone without AI skills; 65% would rather hire a less experienced candidate *with* AI skills.
- TalentCorp impact study: about 620,000 Malaysian workers in 10 sectors, ICT included, will be significantly affected by AI, digital and green-economy changes within 3–5 years. Malaysia launched a National AI Office on 12 Dec 2024.
- Stack Overflow Developer Survey 2025: 84% of developers use or plan to use AI, but 46% distrust its accuracy. The #1 frustration (66%): answers that are "almost right, but not quite".
- METR 2025: experienced developers felt 20% faster with AI but were measured 19% *slower* on real tasks.
- Anthropic 2026 (52 mostly junior developers learning a new library): the AI group scored 50% on the follow-up quiz vs 67% for those who coded by hand. Those who let the AI do everything scored under 40%; those who asked "why?" and questioned the code scored 65% or more.

The lesson: AI makes a pilot faster and a passenger helpless. Pilots **plan, direct, verify and understand**. Passengers accept whatever comes out. Companies hire pilots.

Challenge (Pilot or Passenger?): 4 short scenarios; the player labels each one and says why. Examples:
- "Copies AI code that compiles and pushes it without running the tests." (passenger)
- "Asks the AI why it used a HashMap, then tests an empty input." (pilot)
- "Pastes a customer's full name and IC number into a public chatbot to debug faster." (passenger, and a data leak)
- "Writes 3 steps first, then asks the AI to critique the plan." (pilot)

### Q0.3 Prompt Forge 101

- Teach the 4-part prompt (details in `game/playbooks/ai-pairing.md`): **Goal**, **Context**, **Constraints**, **Verify**, plus the learning add-on "explain your choices".
- Experiment: the player asks you something vague ("explain variables"), then asks the same thing with a 4-part prompt. Compare the two answers: what changed, and why?
- Reveal: "The rules I follow live in `AGENTS.md` in this folder. It's one giant prompt. Open it someday; that's prompting at work."
- The player writes a **Pilot Rules card**: their top 3 rules, in their own words. Save it in the save file.

## Git quests: your save system

Git is how programmers save work: every save point, forever, each with a note saying what changed. GitHub is a website that keeps copies of Git repos online, where teams review and merge work. They're different things: Git works with the Wi-Fi off. Rules and pictures: `game/playbooks/git.md`.

### G0.1 Terminal Basics (after Q0.1)

- Everything Git happens in **Git Bash**. Codex stays in the other window.
- A terminal is a conversation: you type, it answers. Predict each answer first: `pwd` (where am I?), `ls -a` (what's here, hidden things too?), `mkdir practice` (make a folder), `cd practice` (walk in), `cd ..` (walk back out), `git --version`.
- Tips: Tab completes names; the Up arrow brings back earlier commands.

### G0.2 Guild Registration (a GitHub account, in the browser; after Q0.2)

One step at a time:
1. Sign up at https://github.com/signup. Pick a **professional, long-lasting username**: it goes on your CV, and changing it later breaks links. No employer name in it. Verify your email.
2. Turn on two-factor authentication with the authenticator app (GitHub requires it for everyone who contributes code). Save the recovery codes somewhere safe, like a password manager. Add a passkey as a backup.
3. Settings → Emails: tick **Keep my email addresses private** and **Block command line pushes that expose my email**. Copy your private `…@users.noreply.github.com` address for G0.3.
4. Public repos can be seen and copied by anyone, and copies survive even if you later make the repo private. From day one: **no passwords, keys, personal data or company code, ever.**

### G0.3 Sign Your Work (Git settings, once per PC; after G0.2)

For each line, the player says what they think it's for, then runs it:

```bash
git config --global user.name "Your Name"                              # your name on every save point
git config --global user.email "ID+username@users.noreply.github.com"  # your private GitHub email
git config --global init.defaultBranch main                            # new repos start on main
git config --global core.editor "code --wait"                          # messages open in VS Code, not Vim
git config --global pull.ff only                                       # pull never combines histories without asking
git config --global core.autocrlf true                                 # Windows line endings, handled
git config --global alias.graph "log --oneline --graph --all --decorate"   # the map: type git graph
git config --global --list                                             # check everything
```

You check with `git config --get user.email` (read-only).

## Boss: Pilot License

1. Explain pilot vs passenger, with one real data point, in your own words.
2. Write a 4-part prompt for: "Get the AI to explain what a loop is, with an example from my favourite game, and check I understood."
3. State your top 3 pilot rules.
4. Setup check: `git config --global --list` shows your name, your noreply email, `main`, `code --wait` and `pull.ff only`, and you can sign in to GitHub with two-factor authentication.

Pass: all four are clear and correct. Unlocks W1 Atom Valley.

## Lore cards available here

- **LLM**: the AI you're talking to predicts text one piece at a time, from patterns in huge amounts of writing. That's why it can sound sure and still be wrong.
