# How This Works — Concepts

A plain-language explanation of every concept in Business Brain, for when things feel fuzzy.

---

## Chat vs. Agents

A regular AI chat is like a conversation with a stranger. It knows nothing about you unless you tell it right now, and it forgets everything when the chat ends. Every session starts from zero.

An AI agent is different. It reads a set of files at the start of every session — so it already knows its job, your business, and your preferences before you say a word. You are training an employee by writing those files, and that employee gets better the longer you work together.

**Chat = question → answer**
**Agent = goal → result**

The shift sounds small. The compounding effect is not.

---

## The Three Files

### 1. `CLAUDE.md` — The Role Definition

This is the agent's job description. It tells the AI:
- Who it is ("You are the Head of Growth & Sales")
- What its mission is ("Your job is to find and land new clients")
- What files to read before every session
- How to behave

The AI reads this automatically when you open a session in that folder. You never have to re-explain its role.

**Think of it as:** The onboarding document you'd give a new hire on day one.

### 2. `memory.md` — Behavioral Memory

This is where preferences accumulate over time. When you correct the agent ("never sign off with cheers") or state a preference ("always use a casual tone in outreach"), it writes that to `memory.md`. Every new session, the agent reads it first.

The agent doesn't just read it — it uses it. A preference saved once applies forever.

**Think of it as:** The notes a good employee keeps so they don't repeat the same mistake.

### 3. Skills — Standard Operating Procedures

A skill is a step-by-step process, written once, that the agent can run anytime you invoke it. You build a skill by going through a process manually with the agent, then saying: *"Create a skill for what we just did."*

The agent packages the entire process into a skill file. Next time you need it, one command runs it the same way, every time.

**Think of it as:** A standard operating procedure your team can execute without you being there.

---

## The Folder Structure and Why It Works

Each business has a top-level folder (the orchestrator) and subfolders for each department. Each subfolder is a separate agent with its own role and memory.

```
Your Business/           ← Top-level: knows the whole business
  Growth & Sales/        ← Knows client acquisition cold
  Finance/               ← Knows your numbers
  Operations/            ← Knows the production process
```

When you open Claude Code inside a department folder, it reads:
- That department's `CLAUDE.md` (the role)
- That department's `memory.md` (the preferences)
- The parent business `CLAUDE.md` (the broader context)

They stack. The agent has layered context — department-specific and business-wide — without you doing anything.

**Why one agent per department instead of one agent for everything?**

Focus. An agent that's trying to be your head of sales, your CFO, and your ops manager at the same time will be mediocre at all three. An agent that only thinks about client acquisition — with memory specific to outreach, tone, and what's worked — will get dramatically better at that specific job over time.

---

## How Memory Compounds

This is the part most people miss.

Week 1: Memory is empty. You explain preferences constantly.
Week 4: Memory has 10–15 saved preferences. Fewer corrections.
Month 3: Memory has 30–40 preferences and 3–5 skills per department. You stop explaining anything you've done before.
Month 6+: Most of your repeatable work runs automatically. You spend time on judgment calls, not execution.

The error rate goes down. The output quality goes up. The time you spend on each task goes down. This is not linear — it compounds.

---

## Skills Are the Multiplier

Memory reduces errors. Skills eliminate manual work entirely.

Every repeatable process in your business — writing a proposal, analyzing ad performance, following up with leads, reconciling monthly expenses — can become a skill. Once it's a skill:
- It runs the same way every time
- You never explain it again
- You invoke it with one command
- You can chain skills together (morning brief → check inbox → run follow-up skill on open leads)

The question to ask yourself daily: *"Did I just do something I'll do again?"* If yes, turn it into a skill.

---

## Global vs. Department

Some things belong everywhere. Some things belong in one department.

**Department-level (default):** Most skills, most memory preferences. An outreach skill only matters to Growth & Sales. A P&L format only matters to Finance.

**Business-level:** Preferences that apply everywhere. Your name. How you prefer to be addressed. Broad communication style. These go in the top-level `memory.md`.

When in doubt, put it in the department. You can always promote it later.

---

## Harness-Agnostic

Business Brain uses plain markdown files. No platform lock-in.

- **Claude Code:** CLAUDE.md is natively supported. The recommended harness.
- **Codex:** Uses `agents.md` — same concept, different filename.
- **Open Claude / Manus / others:** Same pattern. Check their documentation for the equivalent file name.

The files are yours. They live on your computer. They work with whatever tool you prefer, today or five years from now.

---

## Common Questions

**"Why is the agent asking me things it should already know?"**
It hasn't learned that yet. Correct it — it'll save to `memory.md` and never ask again. Or the relevant file isn't being read; check `CLAUDE.md` to ensure it lists `memory.md` in the "before every session" section.

**"The agent made the same mistake in a new session."**
It didn't save the correction. Say explicitly: *"Remember this. Save it to memory."* Then check that `memory.md` was actually updated.

**"Do I need a new agent for every task?"**
No. One agent per department. Tasks within that department are handled by skills, not new agents.

**"What's the difference between a skill and just asking Claude?"**
Asking Claude does it once, your way, this time. A skill does it the same way, every time, without re-explaining. Skills are for processes you repeat.

**"How do I know when to make something a skill?"**
If you'd do it again — make it a skill. A good rule of thumb: if you find yourself explaining the same process twice, it should have been a skill after the first time.
