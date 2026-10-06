# Playbook: pairing with AI

The goal isn't to avoid AI. It's to be the pilot. Research shows the difference is *how* you use it:
- **Anthropic 2026** (52 mostly junior developers learning a new library): the AI group scored 50% on a follow-up quiz vs 67% for those who coded by hand. Low scorers (under 40%) handed everything to the AI; high scorers (65%+) generated code and then asked why it worked, or asked conceptual questions.
- **Bastani et al. 2025** (PNAS, about 1,000 students): plain GPT-4 raised practice scores by 48%, but those students did 17% worse on the exam without it. A tutor version that gave hints instead of answers avoided the drop.
- **Prather et al. 2024**: struggling novices using AI developed an "illusion of competence": they thought they'd done better than they had.

## The 10 pilot rules

1. **Plan first.** Write your steps or pseudo-code before prompting; let the AI critique the plan.
2. **Generate, then question.** Ask "why this, not that?" until you can explain it.
3. **Debug first, hint second.** Ask for a hint or a question, not the fix.
4. **Explain-back gate.** Commit nothing you can't explain line by line.
5. **Evidence over feelings.** It works only when tests, a build or real output say so. "If you haven't seen it run, it's not a working system." (Simon Willison)
6. **Assume "almost right".** Check edge cases, outdated APIs and security.
7. **One small task per prompt.** After two failed corrections, start a fresh chat with a better prompt.
8. **Touch the code.** Change or extend every generated snippet by hand.
9. **Confidence is not competence.** Quiz yourself without AI; time your tasks.
10. **Vibe-code only toys.** At work: approved tools only, never secrets or personal data.

## Power-ups by world

Same as AGENTS.md section 6: W0–W2 Tutor · W3 Explain-o-scope · W4 Co-pilot · W5 Pilot · W6–W7 Commander. Boss solutions are never AI-written.

## The 4-part prompt

```
Goal:        one sentence: the behaviour you want.
Context:     the file or class, the Java/Spring version, the full error or steps to reproduce.
Constraints: what must not change; ask before adding dependencies.
Verify:      "Run the tests or build and show me the command and its output."
```

Add-ons:
- Examples: inputs and expected outputs, plus one edge case.
- "Explain each change and one alternative you rejected, and why."
- "Propose a plan; don't edit yet." (multi-step work; Codex also has `/plan`)
- "Give me hints, not the answer." (while learning)

Bad → good:
- Bad: "fix my code"
- Good: "Goal: `totalGold()` should return the sum of all items' gold. Context: `Inventory.java`, Java 21; for [10, 20, 5] it returns 30, expected 35. Constraints: keep the method signature. Verify: add a JUnit test for this case and run it. Explain the cause in one sentence."

## Drills

- **Prompt Forge** (Denny et al. 2024): given inputs and outputs, write only the prompt; tests judge the generated code.
- **Almost-Right Hunt**: find the subtle flaw in AI-style code. (66% of developers name "almost right, but not quite" as their top AI frustration: Stack Overflow 2025.)
- **Why-This-Not-That Duel**: defend one of two AI solutions.
- **Diff review**: read an AI change as if you were the senior reviewer. What would you question?

## Data safety (non-negotiable at work)

- Company-approved AI tools only. (In Malaysia, 83% of AI users bring their own AI tools to work, which puts company data at risk: Work Trend Index 2024.)
- Never paste passwords, API keys, tokens, connection strings, or customer or personal data (names, IC numbers, account numbers, addresses, phone numbers).
- Mask before pasting: `<NAME>`, `<IC>`, `<ACCOUNT>`, `<TOKEN>`.
- Company code, configs and logs never go into a personal repo, fork or gist, public or private.
- Unsure? Ask your mentor first.

## Stakes switch (Work Mode)

| Situation | Mode | AI role |
|---|---|---|
| Practice or side task | Full learning | per power-up; hints first |
| Normal ticket | PEAR: Plan → Explore with AI → Analyse every line → Rewrite or explain | per power-up |
| Urgent production bug | Fix first, with the senior's OK | may write the fix; debrief afterwards: what broke, why, how the fix works |
