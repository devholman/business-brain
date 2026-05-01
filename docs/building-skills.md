# Building Skills — Your SOPs for AI

Skills are how this system goes from useful to transformative. This guide covers how to build them, when to build them, and how to chain them together.

---

## What a Skill Is

A skill is a markdown file that captures a step-by-step process. The agent reads it when you invoke the skill and follows it exactly — no re-explaining required.

Every skill lives in a `.claude/skills/[skill-name]/SKILL.md` file, either globally (`~/.claude/skills/`) or inside a project's `.claude/skills/` folder.

---

## When to Build a Skill

Ask yourself after any task: *"Will I do this again?"*

If yes — build a skill. The threshold is low. Even a process that saves you 10 minutes and happens monthly is worth the 5 minutes it takes to create the skill.

Strong signals that something should be a skill:
- You've explained the same process to the agent more than once
- You copied a prompt from a previous session to use it again
- A task took more than 3 back-and-forth messages to complete
- You found yourself saying "like last time" to the agent

---

## Two Ways to Build a Skill

### Method 1 — After a Manual Run (Most Common)

1. Do the process manually with the agent — go back and forth until you're happy with the result
2. Once done, say:
   > "Create a skill for what we just did."
3. The agent packages the full process into a skill file automatically

This is the right method for most skills. You do the process once to discover the steps, then formalize it.

### Method 2 — From Existing Documentation

If you already have a documented process (a written SOP, a training document, a course transcript), upload it and say:
> "Based on this document, create a skill for [process name]."

The agent will extract the steps and structure them into a skill file. You review and adjust.

---

## Anatomy of a Good Skill

```markdown
# /skill-name

One sentence: what this skill does.

## Triggers
"invoke phrase" | "alternate phrase" | /slash-command

## When Invoked
When to run this skill (and when NOT to run it).

## What You Must Do

### Step 1 — [Action Name]
Detailed instructions for this step.

### Step 2 — [Action Name]
...

## Output
What the final output looks like. How to confirm it's done correctly.

## Notes
Edge cases, warnings, things to watch out for.
```

---

## Skill Levels: Department vs. Global

**Department-level skill** — lives inside a project, only applies there.
Use for: anything specific to one business or one department (e.g., `abira-league-outreach`).

**Global skill** — lives in `~/.claude/skills/`, available everywhere.
Use for: things you use across every project (e.g., a writing style skill, a summarizer skill, a daily brief skill).

When in doubt, start department-level. Promote to global if you find yourself wanting it everywhere.

---

## Chaining Skills

Skills can call other skills. This is where the system gets powerful.

Example chain:
```
Morning Brief Skill
  → Check inbox (uses: read-inbox skill)
  → Check calendar (uses: read-calendar skill)
  → If meetings today: run meeting-prep skill for each
  → Summarize priorities for the day
```

To chain skills, the parent skill simply references child skills in its steps:

```markdown
### Step 2 — Prepare for Meetings
If there are any meetings on the calendar today, invoke the `meeting-prep` skill for each one before continuing.
```

Build individual skills first. Chain them once each piece works reliably on its own.

---

## Scheduled Skills

Many agent harnesses now support scheduled tasks — running a skill automatically on a schedule (every morning, every Thursday, the first of each month).

Examples of skills worth scheduling:
- **Daily brief** — every morning at 9am
- **Weekly research digest** — every Thursday
- **Monthly P&L summary** — first of each month
- **Lead follow-up check** — every Monday

Scheduling is harness-specific. In Claude Code, this is handled via the `/schedule` skill. Check your harness documentation for the equivalent.

---

## Skill Naming Conventions

Be specific. A skill named `outreach` is vague. A skill named `abira-league-outreach` tells you exactly what it does and which business it belongs to.

Format: `[business-prefix]-[what-it-does]`

Examples:
- `abira-client-outreach`
- `abira-monthly-pl`
- `abira-order-intake`
- `morning-brief` (global, no prefix)

---

## Growing Your Skill Library

A reasonable pace: build 1–2 skills per week from real work.

After 1 month: 4–8 skills. You've automated the most common processes.
After 3 months: 12–25 skills. Most repeatable work runs automatically.
After 6 months: The processes you still do manually are genuinely novel judgment calls. Everything else is a skill.

The question is never "should I build a skill?" The question is "which process should I skill next?"
