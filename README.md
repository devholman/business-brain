# Business Brain

A template for running your business with AI agents — one agent per department, getting smarter every session.

---

## The Problem

Most people are using AI like a search engine. Ask a question, get an answer, repeat. Every session starts from zero. The AI doesn't know your business, your preferences, or your processes — unless you re-explain them every single time.

That's chat mode. It's useful, but it doesn't compound.

**Agents are different.** An agent reads a set of files before every session. It already knows its role, your business, and your preferences before you say a word. When you correct it, it remembers. When you complete a process, it can package that process into a skill and run it automatically next time.

The longer you work with an agent, the less you have to explain. Errors go down. Speed goes up. The leverage compounds week over week.

**Business Brain** is a template for setting up that system — for any business, any industry, starting today.

---

## What You Get

A folder structure that gives each department of your business its own AI agent:

```
Your Business/
  CLAUDE.md              ← The business orchestrator (who you are, what you do)
  memory.md              ← Business-wide preferences, learned over time

  Growth & Sales/
    CLAUDE.md            ← "You are Head of Growth. Your job is..."
    memory.md            ← Outreach tone, what's worked, what hasn't

  Finance/
    CLAUDE.md            ← "You are Head of Finance. Your job is..."
    memory.md            ← Reporting preferences, expense categories

  Operations/
    CLAUDE.md            ← "You are Head of Operations. Your job is..."
    memory.md            ← Process preferences, vendor notes
```

Each agent knows its job from day one. Each agent remembers your corrections. Each agent can be trained with skills — reusable SOPs that run your repeatable processes automatically.

---

## The 3-File System

Every agent is made of three things:

### 1. `CLAUDE.md` — The Role Definition
The agent's job description. It tells the AI who it is, what its mission is, what to read at the start of every session, and how to behave. Claude reads this automatically when you open a session in that folder.

**Analogy:** The onboarding document you'd give a new hire.

### 2. `memory.md` — Behavioral Memory
Where preferences accumulate over time. When you correct the agent ("never sign off with cheers") or state a preference ("always write outreach in a casual tone"), it writes that to `memory.md`. Every new session, the agent reads it first.

**Analogy:** The notes a good employee keeps so they don't repeat the same mistake.

### 3. Skills — Repeatable Processes (SOPs)
A skill is a step-by-step process, written once, that the agent can run anytime you invoke it. You build a skill by going through a process manually once, then saying: *"Create a skill for what we just did."*

Next time, one command runs the whole process.

**Analogy:** A standard operating procedure your team can execute without you.

---

## The Compounding Effect

| Timeline | What happens |
|---|---|
| Week 1 | Agents know their roles. Memory is empty. You're still explaining preferences. |
| Month 1 | Memory has 10–20 saved preferences. Agents start feeling like they "get you." |
| Month 3 | You've built 3–5 skills per department. Processes that took 20 minutes now run in one command. |
| Month 6+ | Most of your repeatable work is automated. You spend time on decisions, not execution. |

Every correction makes it smarter. Every skill removes a manual process. This is not a tool — it's a system that gets better the longer you use it.

---

## Getting Started

### Option A — Automated Setup (Recommended)

1. Clone this repo and open it in Claude Code:
   ```bash
   git clone https://github.com/YOUR_USERNAME/business-brain
   cd business-brain
   ```

2. Run the setup skill:
   ```
   /new-business-brain
   ```

3. Answer the interview questions. Your full agent structure is created automatically.

### Option B — Manual Setup

1. Copy `templates/business/CLAUDE.md` and `templates/business/memory.md` into a folder named after your business
2. Fill in the placeholders
3. Create a subfolder per department
4. Copy `templates/department/CLAUDE.md` and `templates/department/memory.md` into each
5. Fill in the department-specific role and mission

---

## Template Structure

```
business-brain/
  README.md                          ← You are here
  LICENSE
  .claude/
    skills/
      new-business-brain/
        SKILL.md                     ← Automated setup wizard
  templates/
    business/
      CLAUDE.md                      ← Business orchestrator template
      memory.md                      ← Business-wide memory template
    department/
      CLAUDE.md                      ← Department agent template
      memory.md                      ← Department memory template
  docs/
    concepts.md                      ← How this works (plain language)
    building-skills.md               ← How to create skills from your processes
  examples/
    abira/                           ← Real example: Abira Sports Apparel
```

---

## Real Example: Abira

Abira is a custom sports apparel company for youth and recreational softball teams. Here's how their agent structure is set up:

- **Orchestrator** — knows the full business: products, target market, 12-month plan
- **Growth & Sales** — focused entirely on client acquisition (the #1 open problem)
- **Finance** — tracks revenue vs. targets, margin analysis, cash flow
- **Operations** — manages the order → production → fulfillment pipeline

See `examples/abira/` for the full implementation.

---

## Works With Any Agent Harness

This system uses plain markdown files. It works with any AI agent platform:

- **Claude Code** — recommended (CLAUDE.md is natively supported)
- **Codex** — uses agents.md (same concept)
- **Open Claude / Manus** — same pattern, different file names
- **Any tool that supports a system prompt file**

Once you learn the pattern, you can use it anywhere.

---

## Building Skills

Skills are how this system goes from useful to transformative.

Every time you complete a multi-step process with the agent, ask yourself: *"Will I do this again?"* If yes:

> "Create a skill for what we just did."

The agent packages the process into a skill file. Next time, you invoke the skill and it runs the process the same way, every time.

See `docs/building-skills.md` for a full guide.

---

## Advanced: Knowledge Graph Integration

The core Business Brain system handles **behavior** — what your agents know, remember, and can do. Graphify adds a second layer: **knowledge connections** — automatically mapping the relationships between every note, document, decision, and problem in your business.

These solve different problems and work together.

| Business Brain (CLAUDE.md, memory.md, skills) | Graphify |
|---|---|
| Defines how agents behave | Discovers how knowledge connects |
| Answers: "what does this agent remember?" | Answers: "how does X relate to Y?" |
| Built by working with agents over time | Built automatically from your files |
| Behavioral consistency | Cross-department pattern discovery |

### What Graphify Does

Point graphify at your business folder and it processes every file — markdown notes, operations docs, project overviews, memory files, PDFs, even images. It extracts entities and relationships, clusters them into communities, and produces three outputs:

- **`graph.html`** — an interactive, explorable visualization of everything in your business brain and how it connects
- **`graph.json`** — a queryable graph you can ask questions against in natural language
- **`GRAPH_REPORT.md`** — a written audit of what's in the graph, what's most connected, and what surprising connections were found

### Why This Matters for Business

Your business brain accumulates fast. Within a few months you have department notes, memory files, skills, process docs, and meeting notes — dozens of files across departments. Graphify makes that searchable and connected automatically.

Examples of what you can ask:

```bash
graphify query "what are all the open problems across departments?"
graphify query "how does our pricing strategy relate to customer acquisition?"
graphify query "what has the finance agent learned that's relevant to operations?"
graphify path "production cost" "client retention"
```

Instead of reading five files to piece together a cross-department insight, you ask once and get the connection.

### Setup

```bash
# From your business folder — process all files and build the graph
graphify update .

# Query the graph in natural language
graphify query "what is currently open or in progress?"

# Open the interactive visualization
open graphify-out/graph.html

# Rebuild a navigable wiki from your graph (weekly recommended)
graphify . --wiki
```

After running `graphify update .`, the graph stays current incrementally — only changed files are re-processed on subsequent runs.

### Connecting It to Your Agents

In your business `CLAUDE.md`, add a graphify reference so agents know to use it for cross-department questions:

```markdown
## Knowledge Graph

A graph of this business brain is available at `graphify-out/`.
For cross-department questions or pattern discovery, query it:
`graphify query "your question here"`
```

### The Combined System

```
Business Brain (behavior layer)     Graphify (knowledge layer)
─────────────────────────────────   ─────────────────────────────
CLAUDE.md    → agent knows its role  graph.json  → everything connected
memory.md    → agent remembers prefs graph.html  → visual map of the business
skills       → agent runs SOPs       GRAPH_REPORT → patterns and surprises
```

Used together: your agents behave consistently and learn over time, while graphify gives you a bird's-eye view of your entire business knowledge — automatically updated as you work.

---

## Who This Is For

- Founders and operators running small businesses (1–20 people)
- Anyone who does the same processes repeatedly and wants to stop re-explaining them
- Anyone who's been using chat AI and wants to move to agents

This is not for developers building software products. It's for people who run businesses and want AI to run departments of that business.

---

## License

MIT — use it, share it, build on it.

---

*Built from real use. The Abira example is a working implementation, not a demo.*
