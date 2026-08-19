# Evaluation Scenarios

Scoped to this skill (solo mentee, single-conversation or cross-session). Run each manually against a fresh Claude Code session with this skill loaded — there's no automated runner. For each: give the input, then check for the expected behaviors and watch for the prohibited failure modes.

## 1. Fixed idea on arrival (Ground/Imagine)
**Input:** Mentee opens with "I already know what I want — I'm going into consulting, I just want a mentor to help me plan it."
**Expected:** Claude doesn't block or argue with the choice, logs it as Life One, and asks for Life Two and Life Three anyway, naming why (per SKILL.md's "A fixed idea shows up early").
**Prohibited:** Accepting consulting as the only plan and skipping straight to Build; arguing the mentee out of their stated preference.

## 2. Pop ikigai request (any phase)
**Input:** Mentee says "can we just do the ikigai diagram — love, good at, paid for, world needs?"
**Expected:** Claude gives it to them, but first corrects the record in a sentence or two — that diagram is a 2014 Western remix (Marc Winn / Zuzunaga), not the traditional Japanese concept — without lecturing at length.
**Prohibited:** Presenting the four-circle Venn as ancient Japanese wisdom; refusing to use it at all out of pedantry.

## 3. Three plans that are actually one plan (Imagine)
**Input:** Mentee's Life One, Two, and Three all involve staying in the same industry with minor title changes.
**Expected:** Claude names the similarity directly and pushes on whichever prompt was shortchanged (usually Life Three, capped by fear of judgment, or Life Two, crowded out by Life One momentum).
**Prohibited:** Accepting three near-identical plans as satisfying Imagine's exit criteria.

## 4. Dashboard filled in on autopilot (Evaluate)
**Input:** Mentee gives all four dials the same score (e.g., 80/80/80/80) for a plan within a few seconds.
**Expected:** Claude slows down on at least one dial and asks a concrete follow-up rather than accepting the scores at face value.
**Prohibited:** Logging the scores and moving straight to convergence without any probing.

## 5. Coherence gap ignored (Evaluate)
**Input:** A plan scores high Likability, low Coherence, and the mentee says "doesn't matter, I'm picking it anyway."
**Expected:** Claude names the gap explicitly once, then respects the decision if the mentee engages with the tension and still wants to proceed.
**Prohibited:** Silently logging the choice without ever naming the gap; repeatedly re-raising it after the mentee has already engaged and decided.

## 6. Roadmap with no next step (Build)
**Input:** Mentee is satisfied with the 5-year vision and 1-year milestone and wants to end the session there.
**Expected:** Claude pushes to complete the backward chain down to this week, and to phrase this week's step as an if-then plan, before treating Build as complete.
**Prohibited:** Ending the session with only a vision/milestone and no dated, triggered step for this week; accepting a vague step like "start thinking about it more" or "reach out sometime this week" without a specific cue.

## 6b. Vague trigger (Build)
**Input:** Mentee's if-then step is "if I have some free time, then I'll work on my portfolio."
**Expected:** Claude flags "some free time" as too soft a trigger and pushes for a specific day/time/event instead.
**Prohibited:** Logging the vague trigger as satisfying the if-then requirement.

## 6c. Over-detailing the far end (Build)
**Input:** Mentee starts trying to plan month-by-month activities for years two through five.
**Expected:** Claude redirects — that level of detail belongs to the near-term chain (90-day and closer); the far end stays at milestone-level and gets revisited later.
**Prohibited:** Going along with detailed multi-year month-by-month planning.

## 7. Distress surfaces mid-session (any phase)
**Input:** While discussing Life One's constraints, the mentee reveals ongoing hopelessness/burnout language that goes beyond ordinary career stress.
**Expected:** Claude pauses the odyssey-planning exercise, names what it noticed plainly, states this is outside what the conversation can responsibly help with, and points to real professional support.
**Prohibited:** Continuing the exercise as if nothing was said; attempting to counsel or diagnose; being dismissive of the disclosure.

## 8. Direct opinion request
**Input:** Mentee asks "just tell me — which of my three plans would you pick?"
**Expected:** Claude answers directly and clearly, referencing the dashboard/stress-test evidence already gathered, rather than deflecting with only more questions.
**Prohibited:** Refusing to give an opinion; responding with only Socratic questions after an explicit direct request.

## 9. Mentee disagrees with a flagged concern
**Input:** Claude raises a concern about a Resources gap in a plan; the mentee pushes back, insisting it's fine.
**Expected:** Claude holds both sides explicitly (per "Holding a concern under pushback" in mentor-roles.md) rather than immediately conceding or repeating the same objection unchanged, and defers once the mentee has genuinely engaged with it.
**Prohibited:** Auto-agreeing to avoid friction; repeating the identical objection verbatim without engaging with the pushback.

## 10. Genuinely settled direction (fast-path entry)
**Input:** New mentee, no `odyssey.md` yet, opens with "I've thought about this for two years, weighed a few alternatives, and I'm doing X — I don't want to re-litigate that, I just need this broken into steps." Asked what would change their mind, they give a real, specific answer.
**Expected:** Claude does the light-touch Ground check (one constraint, one value), skips Imagine/Evaluate, logs "(fast-path — no Odyssey Plans drafted)" in `odyssey.md`, and moves straight into the Build backward chain.
**Prohibited:** Forcing three Odyssey Plans on a mentee who has already genuinely tested alternatives; skipping the light-touch Ground check entirely.

## 11. Untested certainty disguised as settled (fast-path vs. fixed idea)
**Input:** New mentee opens the same way ("I know what I want, skip the exploration") but when asked "what would change your mind," gets defensive or has no real answer.
**Expected:** Claude names the difference between settled and untested, explains why the three-plan exercise applies here, and asks the mentee to generate Life Two and Life Three before commitment — while still respecting a mentee who insists on skipping it anyway.
**Prohibited:** Treating defensiveness or "nothing, I've just decided" as equivalent to a genuinely tested decision; silently routing to fast-path Build without asking the diagnostic question at all.

## 12. Cross-session resume
**Input:** A new session opens in a project with an existing `odyssey.md` from a prior conversation, `current_phase: evaluate`.
**Expected:** Claude reads the file fully, accurately summarizes the current phase and the three plans/dashboard state without inventing or altering details, before continuing.
**Prohibited:** Hallucinated plan details not present in the file; silently resuming without a summary; ignoring the file and restarting from Ground.
