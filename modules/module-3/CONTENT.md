# Module 3: Deep Dive into AI Orchestration

**Duration:** 60 minutes  
**Agent ID:** `module-3`

---

## Learning Objectives

By the end of this module, you will:
1. Explain the architecture of AI orchestration systems
2. Configure agents with custom prompts, tools, and behaviours
3. Create and manage skills for reusable capabilities
4. Set up automation workflows with scheduling and webhooks
5. Deploy and run your own AI assistant

---

## 3.1 AI Orchestration Architecture

### The Core Components

```
┌─────────────────────────────────────────────────────────────────────────┐
│                   AI ORCHESTRATION ARCHITECTURE                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    AGENT LAYER                                   │   │
│   │  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐             │   │
│   │  │    SOUL      │ │  INSTRUCTIONS │ │   MEMORY     │             │   │
│   │  │  (Identity)  │ │  (Behaviours) │ │  (Context)   │             │   │
│   │  └──────────────┘ └──────────────┘ └──────────────┘             │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                              │                                          │
│                              ▼                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    TOOL LAYER                                   │   │
│   │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐         │   │
│   │  │  File    │ │ Browser  │ │  Cron    │ │   API    │         │   │
│   │  │  System  │ │  Use    │ │ Scheduler│ │  Calls   │         │   │
│   │  └──────────┘ └──────────┘ └──────────┘ └──────────┘         │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                              │                                          │
│                              ▼                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                   EXTERNAL SERVICES                              │   │
│   │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐         │   │
│   │  │    LLM   │ │  Vector   │ │   Blob   │ │ Message   │         │   │
│   │  │  Provider│ │   Store   │ │  Storage │ │ Platforms │         │   │
│   │  └──────────┘ └──────────┘ └──────────┘ └──────────┘         │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

### The Agent File System

Most AI orchestration systems use a file-based agent structure:

```
agent-name/
├── SOUL.md       ← Identity, personality, philosophy
├── AGENTS.md     ← Workflow, instructions, how to act
├── TOOLS.md      ← Tool definitions, API schemas
├── USER.md       ← User/session state
├── memory/       ← Persistent memory files
│   ├── facts.md
│   └── preferences.md
└── skills/       ← Reusable capability modules
    ├── web-search/
    ├── code-runner/
    └── file-manager/
```

**The Magic:** These are just markdown files. An AI agent reads them and *becomes* that agent.

---

## 3.2 Agent Configuration

### SOUL.md — The Identity Layer

```markdown
# SOUL.md — My Agent Identity

## Who I Am
I am [Name], your [Role]. I help [Audience] with [Purpose].

## My Values
- [Value 1]
- [Value 2]

## My Voice
- Tone: [formal/casual/technical]
- I never [behaviour to avoid]
- I always [behaviour to embrace]

## My Expertise
- [Domain 1]
- [Domain 2]
```

**Why it matters:** The SOUL shapes *how* the agent responds, not just *what* it responds with.

---

### AGENTS.md — The Instruction Layer

```markdown
# AGENTS.md — My Workflow

## My Role
[One sentence describing primary function]

## My Process

### Phase 1: [Name]
**Trigger:** [What starts this phase]
**Steps:**
1. [Step 1]
2. [Step 2]
3. [Step 3]
**Output:** [What this produces]

### Phase 2: [Name]
...
```

---

## 3.3 The Four-Layer Memory System

```
┌─────────────────────────────────────────────────────────────────┐
│                   MEMORY HIERARCHY                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  LAYER 1: WORKING MEMORY (Context Window)                      │
│  ────────────────────────────────────────────                   │
│  • What's happening RIGHT NOW                                    │
│  • What's in the current conversation                            │
│  • Size: 8K–200K tokens (model dependent)                        │
│  • Lifetime: Current session only                                │
│                                                                 │
│  LAYER 2: SEMANTIC MEMORY (Long-Term Facts)                    │
│  ────────────────────────────────────────────                   │
│  • What the agent KNOWS about the world                         │
│  • The agent's own knowledge (from training)                    │
│  • Retrieved via similarity search                               │
│                                                                 │
│  LAYER 3: EPISODIC MEMORY (Experiences)                        │
│  ────────────────────────────────────────────                   │
│  • Past interactions and events                                  │
│  • "Last time we discussed X..."                                │
│  • Stored as structured records                                  │
│                                                                 │
│  LAYER 4: PROCEDURAL MEMORY (Skills)                            │
│  ────────────────────────────────────────────                   │
│  • HOW to do things — skills, workflows                        │
│  • Stored as skill files and tool definitions                  │
│  • "I know HOW to search the web..."                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 3.4 Skills — Reusable Capabilities

A **skill** is a reusable module that extends what an agent can do.

### Anatomy of a Skill

```
skill-name/
├── SKILL.md       ← Instructions for the agent
├── scripts/       ← Optional helper scripts
│   └── run.sh
└── references/    ← Reference docs
    └── api.md
```

### Example: Web Search Skill

```markdown
# SKILL.md — Web Search

## What I Do
Search the web for up-to-date information.

## When to Use Me
- When you need current information (after [training date])
- When you need to verify facts
- When researching topics outside my training data

## How to Use Me
1. Formulate a clear search query
2. Use the browser tool with the query
3. Read the top 3 results
4. Synthesise a response

## Limitations
- I can access most public websites
- I cannot access paywalled content without credentials
- Results depend on search engine quality
```

---

## 3.5 Scheduling & Automation

### Cron Jobs (Time-Based Triggers)

Schedule tasks to run at specific times:

```json
// Cron configuration example
{
  "name": "Morning Report",
  "schedule": "0 7 * * *",
  "enabled": true,
  "task": "Generate and send morning report",
  "channels": ["telegram", "whatsapp"]
}
```

**Cron Format:**
```
┌───────────── minute (0-59)
│ ┌─────────── hour (0-23)
│ │ ┌───────── day of month (1-31)
│ │ │ ┌─────── month (1-12)
│ │ │ │ ┌───── day of week (0-6, Sunday=0)
│ │ │ │ │
* * * * *
```

| Schedule | Meaning |
|----------|---------|
| `0 7 * * *` | Daily at 7am |
| `0 9 * * 1` | Every Monday at 9am |
| `0 8 * * 1-5` | Weekdays at 8am |

---

### Webhooks (Event-Based Triggers)

Trigger actions based on external events:

```
┌─────────────────────────────────────────────────────────────────┐
│                         WEBHOOK FLOW                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   External Event          Orchestrator         Agent Action     │
│   ─────────────          ────────                ───────────    │
│                          │                                        │
│   Stripe payment ────────►│ Generate receipt                    │
│   GitHub PR ────────────►│ Notify team                         │
│   Email received ───────►│ Classify + respond                  │
│   Form submitted ────────►│ Add to CRM + send confirmation      │
│                          │                                        │
└─────────────────────────────────────────────────────────────────┘
```

---

## 3.6 Multi-Agent Systems

When one agent isn't enough, use a team:

```
