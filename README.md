<h1 align="center">Odyssey Mentor</h1>

<p align="center">
  A structured life and career mentoring skill for Claude Code — moves a person from uncertainty to a chosen direction and a dated next action, using named, cited frameworks rather than generic encouragement.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/type-Claude_Code_Skill-5A31F4" alt="Claude Code Skill">
  <img src="https://img.shields.io/badge/framework-Odyssey_Plan_%2B_GROW_%2B_Graduate_Capital-blue" alt="Frameworks">
  <img src="https://img.shields.io/badge/sources-8_cited-informational" alt="8 cited sources">
  <a href="./LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" alt="MIT License"></a>
</p>

<p align="center">
  <a href="#what-it-does">What it does</a> ·
  <a href="#install-add-it-to-your-skills-arsenal">Install</a> ·
  <a href="#how-it-works">How it works</a> ·
  <a href="#framework--sources">Sources</a> ·
  <a href="#build-your-own-skills-this-way">Build your own</a> ·
  <a href="#license">License</a>
</p>

---

## What it does

Career-mentoring prompts typically amount to a personality wrapped around generic encouragement. This skill is a process instead: four phases (Ground → Imagine → Evaluate → Build), each backed by a named framework, each with explicit exit criteria, and a state file (`odyssey.md`) that persists across sessions so the work survives beyond a single conversation.

<table>
<tr>
<th width="50%">Unstructured prompting</th>
<th width="50%">Odyssey Mentor</th>
</tr>
<tr>
<td valign="top">

> "It sounds like you're feeling stuck. Have you considered making a pros and cons list, or talking to people in fields you're interested in? Following your passion while being practical is important. What matters most to you?"

</td>
<td valign="top">

> "Before we look at options — what's something ordinary you'd genuinely miss if it disappeared from your week? Not resume-worthy, just real. That pattern usually predicts what makes a plan livable better than a job title does."
>
> *(Ground phase — authentic ikigai reflection, not the four-circle Venn)*

</td>
</tr>
</table>

The skill also corrects a widely repeated inaccuracy: the "ikigai" Venn diagram (love / good at / paid for / world needs) is not traditional Japanese thought — it is a 2014 Western remix of a 2011 diagram. This skill applies the authentic concept instead, and states the correction explicitly. See [`references/ikigai.md`](references/ikigai.md).

> [!NOTE]
> This is direction-level clarity work — figuring out *what* to pursue and the first real step toward it. It is not a CV/interview-mechanics tool or a single tactical decision-maker.

## Install: add it to your skills arsenal

Once this repository is published on GitHub:

```bash
npx skills add DasonTiovino/odyssey
```

This installs through [`skills`](https://github.com/vercel-labs/skills), a standard package manager for agent skills. It fetches `SKILL.md` from the given repository and places it in `~/.claude/skills/` (or the equivalent directory for other compatible agents). It requires the repository to be pushed to GitHub — a local, unpublished folder has nothing for the command to fetch.

<details>
<summary><strong>Installing before publishing, or from a local copy</strong></summary>

Claude Code auto-discovers skills from `~/.claude/skills/` directly — any folder there with a valid `SKILL.md` becomes available immediately, with no separate registration step:

```bash
# 1. Land the whole skill folder under ~/.claude/skills/
cp -r /path/to/odyssey-mentor ~/.claude/skills/odyssey-mentor

# 2. Verify the frontmatter is intact
head -n 3 ~/.claude/skills/odyssey-mentor/SKILL.md

# 3. Start (or restart) a Claude Code session — it should list `odyssey-mentor`
#    in its available-skills context automatically.
```

To keep the installed copy git-tracked and publishable rather than a static duplicate, symlink it instead of copying:

```bash
ln -s /path/to/your/odyssey-mentor-repo ~/.claude/skills/odyssey-mentor
```

</details>

**Using it:**

```
/odyssey-mentor
```

or just describe what you need in plain language ("I don't know what I want to do with my career," "help me build an odyssey plan," "I know what I want but I need it broken into steps") — the skill's `description` field is written to trigger on intent, not just the slash command.

The skill creates `odyssey.md` in whatever project directory you're working in when you first invoke it. That file *is* the mentoring record — reopen the same project later and the skill picks up exactly where it left off.

> [!IMPORTANT]
> This skill is portable, not framework-locked to Claude Code specifically. `SKILL.md`'s YAML frontmatter (`name` + `description`) plus a linked `references/` folder is a convention several agent runtimes recognize (Claude Code, and skills-compatible tooling for other agents). If your agent uses a different skills directory, the install step is the same idea: copy the folder, point the agent at it.

## How it works

| Phase | Question it answers | Framework | Exit looks like |
|---|---|---|---|
| **Ground** | Who are you, actually — not your resume? | Graduate Capital Model (Tomlinson, 2017) + authentic ikigai (Mogi) | 2-3 confident values with real examples, named constraints |
| **Imagine** | What are the genuinely different lives you could live? | Odyssey Plan method (Burnett & Evans, *Designing Your Life*) | Three 5-year plans that actually differ, each with non-career milestones |
| **Evaluate** | Which one, and why? | Burnett & Evans's Resources/Likability/Confidence/Coherence dashboard + GROW (Whitmore) | A chosen direction with a stated reason, stress-tested against reality |
| **Build** | What do you actually do this week? | Locke & Latham's proximal-goal chaining + Gollwitzer & Oettingen's implementation intentions | A backward-built chain down to an if-then step with a date |

Already know your destination? There's a fast path straight into Build that skips Imagine/Evaluate — see "Already decided vs. not yet tested" in [`SKILL.md`](SKILL.md).

Throughout, the mentor keeps a hard boundary: it's mentoring, not therapy. If real distress surfaces, the skill stops the exercise and points to professional support rather than improvising counsel. See [`references/mentor-roles.md`](references/mentor-roles.md).

<details>
<summary><strong>Full file structure</strong></summary>

```
odyssey-mentor/
├── SKILL.md                       # Orchestrator: phase cycle, routing, boundaries
├── README.md                      # This file
├── references/
│   ├── intake.md                  # Ground phase
│   ├── odyssey-plan.md            # Imagine phase — the three plans
│   ├── ikigai.md                  # Ikigai, used honestly (origin + authentic concept)
│   ├── evaluate.md                # Evaluate phase — dashboard + GROW stress-test
│   ├── build.md                   # Build phase — proximal chain + if-then steps
│   ├── mentor-roles.md            # Boundaries, question taxonomy, escalation
│   └── odyssey-artifact.md        # odyssey.md template + update rules
└── evals/
    └── scenarios.md               # 12 manual test scenarios covering every guardrail
```

</details>

## Framework & sources

Every behavioral rule in this skill traces to a named source — evidence over vibes was a hard requirement while building it.

| Source | Used for |
|---|---|
| Tomlinson, M. (2017). *The Graduate Capital Model.* | Ground phase's five-capital self-inventory |
| Burnett, B. & Evans, D. (2016). *Designing Your Life.* Stanford d.school. | The three-plan Odyssey method and its scoring dashboard |
| Whitmore, J. *The GROW Model.* | Evaluate phase's Reality/Options stress-test; the mentor intervention ladder |
| University of Southampton Career Mentoring Handbook. | Mentor DOES/MUST NOT boundaries, the six-type question taxonomy, structured meeting cadence |
| Locke, E. & Latham, G. *Goal Setting Theory* (~400 studies). | Build phase's backward chain of proximal subgoals |
| Gollwitzer, P. & Oettingen, G. *Implementation Intentions* / WOOP. | Build phase's if-then step formatting |
| Zuzunaga, A. (2011) *Purpose* diagram; Winn, M. (2014) blog remix. | Correcting the popular ikigai Venn's actual (Western, recent) origin |
| Mogi, K. *Five pillars of ikigai.* | The authentic small-daily-things ikigai reflection actually used in Ground |

Full citations and how each is applied are inline in the relevant `references/*.md` file, not restated here — read the phase file if you want the reasoning, not just the name.

## Build your own skills this way

If you're extending your own arsenal beyond this one skill, the pattern that held up here:

1. **Lean `SKILL.md`, fat `references/`.** The orchestrator should be short enough to read in one pass — phase list, routing logic, links out. Depth belongs in linked files loaded on demand, not inline.
2. **Frontmatter `description` is the trigger.** Write it to include the phrases someone would actually say ("I don't know what I want," not just "career mentoring"), plus what it's *not* for — that second part prevents false-positive triggering.
3. **Persist state to a file, not the conversation.** Anything that needs to survive a compacted or new session belongs in a project-root artifact file with a template and explicit update rules — see [`references/odyssey-artifact.md`](references/odyssey-artifact.md) for the pattern.
4. **Name the anti-patterns, not just the happy path.** Every phase file here has an "Anti-patterns" section naming the specific failure mode and the exact redirect — that's what turns a vague instruction into a followable one.
5. **Write eval scenarios before you trust it.** [`evals/scenarios.md`](evals/scenarios.md) — input, expected behavior, prohibited behavior, run manually against a fresh session. Low-cost verification against a skill that reads correctly but behaves incorrectly.
6. **Cite before you assert.** If a skill leans on a named framework, verify it (don't recall it from training data alone) and correct it in the skill itself when the popular version is wrong — see [`references/ikigai.md`](references/ikigai.md) for what that looks like in practice.

## License

[MIT](./LICENSE) — the skill's instructions and templates are free to copy, adapt, and redistribute. The cited frameworks (Odyssey Plan, GROW, Graduate Capital Model, etc.) remain the intellectual property of their original authors; this skill applies and references them, it doesn't republish their source material.
