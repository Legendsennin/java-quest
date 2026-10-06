# Playbook: when the player is stuck

Being stuck is the job, not a sign you're bad at it. A field study of professional developers found they spend about 58% of their time understanding code (Xia et al. 2018). The skill is getting unstuck systematically.

## The protocol (in order)

1. **Name it plainly**, in one sentence, no hype. "This one's fighting back. NullPointerExceptions confuse everyone the first few times."
2. **One real story** from the bank below that matches the moment: the struggle is common and temporary. Two lines max, then move on.
3. **Restate** (the player does this): the goal, expected vs actual, exact steps to reproduce. CS50's two questions: "What is working? What is not working?"
4. **Evidence**: the error message → the last "Caused by" → the first line in *our* code → matching log lines. (`game/playbooks/debugging.md`)
5. **Hypothesis**: the player writes a hypothesis, a prediction and one experiment, then logs the result.
6. **Still lost? Trace**: line by line, with a variable table.
7. **Hint ladder** (one rung per `hint`):
   1. A question that points at the gap.
   2. A pointer: the file and line to look at.
   3. A partial worked example of a similar problem.
   4. The full solution; the player explains it back in their own words and redoes a similar task later.
8. **AI as a partner, not a vending machine**: the player writes the prompt (goal, expected vs actual, stack trace, what they tried). The AI suggests hypotheses, not patches.
9. **Long block** (at work, for example, 30+ minutes on one problem): draft a message to their mentor together, with the debug log attached. Asking a human well is a skill, not a failure.
10. **Close**: replay the cause, the step that cracked it, and one rule to keep. Record the win in the save file.

## Rules

- Never say "you've got this" without a concrete next step attached.
- Byte takes the blame for planted bugs. The player is never "wrong", only "not yet".
- "Save and come back tomorrow" is a valid move. Save first.
- One step at a time. Don't flood.
- If frustration is rising, shrink the problem: "Can you make it fail in 3 lines?"

## Story bank (verified; one at a time, 2 lines max)

| When | Story | Source |
|---|---|---|
| Frustrated by bugs | Maurice Wilkes, who built one of the first stored-program computers, 1949: he realised "a good part of the remainder of my life was going to be spent in finding errors in my own programs." | https://en.wikiquote.org/wiki/Maurice_Wilkes |
| First bug hunt | In 1947 the Harvard Mark II team found a moth in a relay and taped it into the logbook: "First actual case of bug being found." Grace Hopper was on the team and made the story famous; she didn't invent the word. | https://www.computerhistory.org/tdih/september/9/ |
| "Debugging is so hard" | Brian Kernighan, co-author of the classic C book: "debugging is twice as hard as writing a program in the first place." It's supposed to be hard. | https://en.wikiquote.org/wiki/Brian_Kernighan |
| "Nobody taught me this" | Andreas Zeller, who wrote a textbook on debugging: "I never got any formal training in debugging, so I had to figure this out for myself." | https://www.debuggingbook.org/html/Intro_Debugging.html |
| "I'll never figure this out" | Julia Evans, a well-known engineer and writer: when "it feels like I'll NEVER make progress", she reminds herself "I've fixed a lot of bugs before, and I'll probably fix this one too." | https://web.archive.org/web/2023/https://jvns.ca/blog/2022/12/08/a-debugging-manifesto/ |
| Feeling like a fake | Scott Hanselman's mentee graduated at the top of their CS degree, got into Microsoft, and still felt like "an imposter." Hanselman: "We all feel like phonies sometimes… That's how we grow." | https://web.archive.org/web/2023/https://www.hanselman.com/blog/im-a-phony-are-you |
| "Everyone else knows this" | Dan Abramov, who helped build React, published a list of things he didn't know, including: "I can ls and cd but I look up everything else." | https://web.archive.org/web/2024/https://overreacted.io/things-i-dont-know-as-of-2018/ |
| Looking things up | DHH, creator of Ruby on Rails: "I would fail to write bubble sort on a whiteboard. I look code up on the internet all the time." | https://twitter.com/dhh/status/834146806594433025 |
| "My code is ugly" | Ira Glass: for years your taste is ahead of your skill, and "your taste is why your work disappoints you." The fix: "do a lot of work." | https://numerocinqmagazine.com/2011/05/13/what-nobody-tells-beginners-ira-glass-on-storytelling/ |
| Lost in old code | Joel Spolsky: "It's harder to read code than to write it." The ugly bits in old code are often bug fixes someone paid for. | https://web.archive.org/web/2024/https://www.joelonsoftware.com/2000/04/06/things-you-should-never-do-part-i/ |
| Afraid to fail | Mark Rober's Super Mario Effect: 50,000 people played a coding puzzle. With no penalty for failing, about 68% succeeded; with a small penalty, about 52%. The no-penalty group tried about 2.5 times as often. | https://www.ted.com/talks/mark_rober_the_super_mario_effect_tricking_your_brain_into_learning_more/transcript |
| "AI makes me feel fast" | METR 2025: experienced developers felt 20% faster with AI but were measured 19% slower. Feeling isn't evidence. | https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/ |
