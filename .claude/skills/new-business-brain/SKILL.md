# /new-business-brain

Interview a founder and scaffold their full Business Brain agent structure — business orchestrator, department agents, and memory files — all populated with real context.

## Triggers

"/new-business-brain" | "set up my business brain" | "create my agent structure"

## When Invoked

Run this skill when any trigger appears. Do not ask for confirmation — just start the interview.

## What You Must Do

### Step 1 — Interview (one question at a time)

Ask each question and wait for the answer before moving on. Confirm if the answer is ambiguous.

1. **What's the name of your business?**

2. **What do you sell or do?** (1–2 sentences — be specific)

3. **What is your #1 goal or open problem right now?** (The thing keeping you up at night or the most important thing to solve)

4. **Which departments do you want agents for?**

   Show these suggestions and let them pick any combination, add their own, or skip any:
   - Growth & Sales (client acquisition, outreach, proposals)
   - Finance (revenue, expenses, margins, cash flow)
   - Operations (orders, production, fulfillment, vendors)
   - Marketing (content, social media, brand, campaigns)
   - Customer Success (onboarding, retention, support)
   - Product (roadmap, feature prioritization, feedback)

5. **For each department they selected:** "In one sentence, what is the [Department] agent's primary job?"

   Ask this for each department individually — don't batch them.

### Step 2 — Confirm before building

Print a summary of what you're about to create:

```
Here's what I'll build:

Business: [Name]
What you do: [summary]
Open problem: [problem]

Departments:
- [Department 1]: [mission]
- [Department 2]: [mission]
...

Creating this structure in the current directory. Confirm?
```

Wait for confirmation before proceeding.

### Step 3 — Create the folder structure

```bash
mkdir -p "[Business Name]"
mkdir -p "[Business Name]/[Department 1]"
mkdir -p "[Business Name]/[Department 2]"
# ... one mkdir per department
```

### Step 4 — Write the business orchestrator files

**`[Business Name]/CLAUDE.md`:**

```markdown
# [Business Name] — Business Orchestrator

You are the top-level context for [Business Name]. This file gives you the business overview. For department-specific work, navigate to the relevant department folder — each has its own agent context and memory.

---

## Before Every Session

Read these files:

1. `memory.md` — business-wide preferences learned across sessions

---

## Business at a Glance

- **What:** [what they do]
- **Open Problem #1:** [their stated open problem]

---

## Department Agents

Each department has its own folder, `CLAUDE.md`, and `memory.md`. Open the relevant folder to work with that agent.

| Department | Folder | Mission |
|---|---|---|
[one row per department: | Department | Folder Name | mission |]

---

## Working Style

- Be direct and practical
- For business-wide preferences, update `memory.md`
- For department-specific preferences, update the relevant department's `memory.md`

---

## Updating Business-Wide Memory

When a correction or preference applies across departments:
1. Complete the task
2. Open `memory.md` and update the relevant section
3. Say: "Saved to memory: [preference]"
```

**`[Business Name]/memory.md`:**

```markdown
---
project: [Business Name]
author: claude
date: [today's date]
---

# [Business Name] Memory

Business-wide preferences learned across sessions. Read at the start of every session.

---

## Business Preferences

*Nothing saved yet.*

## Communication Preferences

*Nothing saved yet.*
```

### Step 5 — Write each department's files

For each department, write two files:

**`[Business Name]/[Department]/CLAUDE.md`:**

```markdown
# [Business Name] — [Department Name]

You are [Devyn]'s [Department Name] agent for [Business Name]. [Mission sentence from interview.]

---

## Before Every Session

Read these files before any task:

1. `../CLAUDE.md` — full business context
2. `memory.md` — [department] preferences learned across sessions

---

## Your Focus

[Mission sentence]. Keep every task connected to this goal.

---

## Updating Memory

When corrected or given a preference:
1. Complete the task
2. Open `memory.md` and update the relevant section
3. Say: "Saved to memory: [preference]"

---

## Available Skills

*(None yet — build skills as processes repeat. After doing something manually: "Create a skill for what we just did.")*
```

**`[Business Name]/[Department]/memory.md`:**

```markdown
---
project: [Business Name]
department: [Department Name]
author: claude
date: [today's date]
---

# [Department Name] Memory

Preferences and corrections for [Department Name] work. Read at the start of every session.

---

## Preferences

*Nothing saved yet.*
```

### Step 6 — Print confirmation

```
Business Brain created for [Business Name].

Structure:
  [Business Name]/
    CLAUDE.md              ← Business orchestrator
    memory.md              ← Business-wide memory
    [Department 1]/
      CLAUDE.md
      memory.md
    [Department 2]/
      CLAUDE.md
      memory.md
    ...

Next steps:
1. Open a department folder in Claude Code to start working with that agent
2. Work through your first real task manually — then say "create a skill for what we just did"
3. Back this up: git init → create a GitHub repo → git push

The system grows as you use it. Every correction saves to memory. Every repeated process becomes a skill.
```

## Path Reference

Creates the business folder in the current working directory.
