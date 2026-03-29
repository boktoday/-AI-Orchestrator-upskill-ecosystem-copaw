# Projects — Hands-On Learning

These projects let you apply what you've learned in Modules 1–4. Choose the one that best fits your role, industry, or interest.

---

## Project 1: Personal Productivity Agent

**Difficulty:** ⭐ Beginner  
**Time:** 2–3 hours  
**Platform:** Any AI orchestration tool

### Brief
Design and build a personal AI agent that handles your most repetitive daily tasks.

### Requirements
- Define the agent's SOUL.md (identity)
- Design 3 automated workflows in AGENTS.md format
- Specify 2–3 tools the agent needs
- Write out one full workflow as a step-by-step process

### Example Outputs
- A "Morning Briefing" agent that checks your calendar, weather, news, and emails — then sends you a single summary
- A "Meeting Prep" agent that researches attendees, finds relevant docs, and generates talking points
- A "Inbox Zero" agent that triages, drafts replies, and escalates urgent items

---

## Project 2: Multi-Agent Customer Service Team

**Difficulty:** ⭐⭐ Intermediate  
**Time:** 4–6 hours  
**Platform:** CoPaw, LangChain, or CrewAI

### Brief
Design a team of 3 specialised AI agents that handle customer support together.

### Agent Roles
| Agent | Specialty | What It Does |
|-------|-----------|--------------|
| **Triage Agent** | First contact | Reads complaint → categorises → routes |
| **Resolution Agent** | Problem-solving | Researches solutions → drafts response |
| **Escalation Agent** | Complex cases | Identifies when human needed → flags |

### Requirements
1. SOUL.md for each agent
2. Workflow showing how they communicate
3. Decision logic for escalation
4. Memory architecture (what does each agent remember?)
5. One complete example: a customer complaint → resolution

---

## Project 3: AI-Powered Research Assistant

**Difficulty:** ⭐⭐⭐ Advanced  
**Time:** 6–8 hours  
**Platform:** CoPaw or LangChain

### Brief
Build an agent that can research a topic deeply and produce a structured report.

### The Research Loop
```
User asks question
       │
       ▼
┌──────────────────┐
│  Plan research   │
│  strategy        │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│  Web search × N  │
│  (iterative)     │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│  Synthesise     │
│  findings       │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│  Generate        │
│  structured      │
│  report          │
└──────────────────┘
```

### Requirements
1. Full SOUL.md for the research agent
2. AGENTS.md with the research loop implemented
3. TOOLS.md specifying: web search, reading, note-taking
4. Example: Research "AI agents in healthcare" → produce a 5-section report
5. Evaluation: How would you measure the quality of the output?

---

## Project 4: AI Ethics Audit

**Difficulty:** ⭐⭐ Intermediate  
**Time:** 3–4 hours (research + writing)  
**Platform:** Any

### Brief
Choose an existing AI product (e.g., a customer service chatbot, a hiring tool, a recommendation engine) and conduct a full ethics audit.

### Framework to Apply

**1. Fairness**
- Who benefits? Who might be harmed?
- Are there bias risks?
- How are edge cases handled?

**2. Transparency**
- Can users tell they're talking to AI?
- Can decisions be explained?
- Is there an appeals process?

**3. Privacy**
- What data is collected?
- How is it stored and protected?
- Does the user consent?

**4. Safety**
- What safeguards exist?
- What happens if something goes wrong?
- How is harmful content prevented?

**5. Human Oversight**
- Can humans intervene?
- Is there a human in the loop?
- How are errors corrected?

### Deliverable
A 2–3 page "AI Ethics Audit Report" covering all 5 areas, with specific recommendations.

---

## Project 5: AI ROI Calculator

**Difficulty:** ⭐⭐ Intermediate  
**Time:** 2–3 hours  
**Platform:** Any (spreadsheet or code)

### Brief
Build an ROI calculator for an AI agent implementation in a specific scenario.

### The Calculator Should Include

**Inputs:**
- Hours saved per week
- Average hourly cost ($/hr)
- Number of errors reduced (per week)
- Average cost per error
- AI implementation cost ($/month)
- API/usage costs ($/month)

**Outputs:**
- Monthly cost savings
- Annual ROI (%)
- Break-even timeline
- 5-year projected savings

### Deliverable
Either:
- A spreadsheet with formulas
- OR a Python script that calculates and displays results
- Plus a 1-page summary of assumptions and findings

---

## How to Submit

1. Complete your chosen project
2. Share it with your coach
3. Present your approach and findings in our next session
4. Get feedback and iterate

---

*These projects are designed to be real. Use real tools, real data, real problems. The best learning happens when you build something you'd actually use.*
