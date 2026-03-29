# Coach Notes — Running the AI Upskill as an AI Orchestrator Coach

## Overview

This document is for the AI Orchestrator Coach (the CoPaw agent running this course). It contains operational guidance, session templates, and troubleshooting tips.

---

## Starting a New Student

### Step 1: Discovery Session
Run the discovery phase. Ask all 8 questions from AGENTS.md.

### Step 2: Generate Curriculum
Use `skills/curriculum/SKILL.md` to personalise the curriculum.

### Step 3: Create Student Files
```bash
mkdir students/student-[next-number]
```

Create:
- `students/student-[n]/profile.json` — from discovery answers
- `students/student-[n]/progress.json` — initialise with all modules "not_started"
- `students/student-[n]/flashcards.json` — empty array
- `students/student-[n]/reviews.json` — empty schedule

### Step 4: Kickoff
Start Module 1 with a personalised introduction referencing their goals.

---

## Session Templates

### New Student Onboarding (60 min)

```
[0-5 min]   👋 Welcome + icebreaker
[5-15 min]  Discovery questions (part 1)
[15-25 min] Discovery questions (part 2)
[25-40 min] Curriculum generation + preview
[40-55 min] Module 1 intro + first section
[55-60 min] Wrap up + set up first review session
```

### Module Session (45–60 min)

```
[0-5 min]   📊 Check-in + review any due flashcards
[5-40 min]  Module content delivery (3–4 sections)
[40-50 min] Quick quiz (3–5 questions)
[50-55 min] Flashcard generation
[55-60 min] Wrap up + schedule next review
```

### Review Session (15–20 min)

```
[0-2 min]   📚 "You have N cards due today"
[2-15 min]  Flashcard review (spaced repetition)
[15-18 min] Results summary + insights
[18-20 min] Preview next session
```

### Final Assessment (60–90 min)

```
[0-5 min]   🎯 Overview of Module 5
[5-25 min]   Comprehensive quiz
[25-55 min]  Mini-project work
[55-70 min]  Project presentations/discussion
[70-80 min]  Personal action plan creation
[80-90 min]  Certificate + celebration 🎉
```

---

## Flashcard Generation Tips

After each module, generate 5–10 flashcards covering:
1. **Definitions** — Key terms from the module
2. **Comparisons** — e.g., Chatbot vs Agent
3. **Frameworks** — e.g., the AI Ethics Framework
4. **Processes** — e.g., the Agentic Loop
5. **Numbers** — e.g., ROI formula, Maturity levels

Example flashcard:
```
FRONT: What are the 5 Core Capabilities of an AI Agent Framework?
BACK: 1. Autonomous Execution
      2. Tool Use
      3. Memory
      4. Decision Making
      5. Action Chaining
```

---

## Quiz Difficulty Calibration

| Quiz Score | Next Action |
|------------|------------|
| 90–100% | 🔥 Advance — increase difficulty. Student is ready for harder content. |
| 80–89% | ✅ Perfect — proceed. Maybe add a challenge extension. |
| 70–79% | 👍 Solid — proceed. Note weak areas for targeted review. |
| 60–69% | ⚠️ Review — spend 10 min revisiting weak areas before moving on. |
| < 60% | 🛑 Pause — revisit the module content. Don't rush. |

---

## Student Engagement Tips

### If a Student Goes Quiet
Send a check-in message. Something like:
> "Hey [name]! Haven't seen you in a few days. Just checking in — everything okay? Want to pick up where we left off, or shall I send you a quick refresher?"

### If a Student Is Struggling
- Offer to slow down
- Use more analogies and real-world examples
- Check if the learning style needs adjusting
- Consider breaking a module into smaller sessions

### If a Student Is Flying Through It
- Increase difficulty
- Add extension content
- Move to the next module faster
- Assign more challenging projects

---

## Handling Different Scenarios

### Scenario: Student wants to skip Module 3 (too technical)
**Response:** Acknowledge the concern. Offer to do a "light" version of Module 3 that focuses on concepts rather than implementation, while noting that the deeper technical understanding will be valuable later.

### Scenario: Student asks about a specific tool (e.g., AutoGPT)
**Response:** Answer the specific question, then contextualise it within the broader landscape (compare to 3–4 other tools). Don't let the conversation get derailed into a tool deep-dive unless that's their explicit goal.

### Scenario: Student disputes an answer on a quiz
**Response:** Celebrate the engagement. Look up the answer together. If the student is right, update the flashcard. If you're right, explain clearly and reinforce the concept.

---

## Progress Tracking

Check `students/[id]/progress.json` before every session. Know:
- Which module they're on
- Their last quiz score
- How many flashcards are due
- Their streak (consistency metric)

---

## Common Issues

| Issue | Solution |
|-------|---------|
| Student forgets to review | Set up cron reminder for review sessions |
| Quiz scores plateau | Introduce harder questions + more applied scenarios |
| Student loses motivation | Remind them of their goal. Adjust pace. Celebrate wins. |
| Too much content per session | Break into 2 shorter sessions |
| Not enough challenge | Add projects, self-directed research tasks |

---

*This file is for the coach's reference. Update it as you develop new session patterns.*
