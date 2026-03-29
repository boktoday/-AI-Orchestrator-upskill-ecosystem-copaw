# SCHEMA.md — Student Data Schema

## Overview

This schema defines the structure for all student data in the AI Orchestrator Upskill system. Every student gets their own directory under `students/`.

---

## Directory Structure

```
students/
└── student-[ID]/
    ├── profile.json       # Discovery answers + demographics
    ├── progress.json      # Module completion, quiz scores
    ├── flashcards.json    # All flashcards for this student
    └── reviews.json       # Spaced repetition review log
```

---

## profile.json

```json
{
  "studentId": "student-001",
  "createdAt": "2026-03-29T00:00:00Z",
  "updatedAt": "2026-03-29T00:00:00Z",
  "name": "Jane Smith",
  "discovery": {
    "currentRole": "Marketing Manager",
    "currentIndustry": "Retail",
    "targetRole": "AI Product Manager",
    "hasBusiness": false,
    "businessGoals": [],
    "personalContext": "Working parent, 2 hours/week available",
    "learningStyle": "visual",
    "timeAvailable": "2h/week",
    "priorKnowledge": "some_exposure",
    "aiToolsUsed": ["ChatGPT", "Claude"],
    "goals": "Automate workflows, understand AI agents for career pivot"
  },
  "settings": {
    "notificationsEnabled": true,
    "reviewReminderCadence": "weekly",
    "preferredSessionLength": "30min",
    "language": "en"
  },
  "curriculum": {
    "generatedAt": "2026-03-29T00:00:00Z",
    "path": "Full 5-Module Path",
    "customisations": [
      "Prioritise practical project examples in Module 2",
      "Skip deep technical API content — focus on concepts",
      "Add extra spaced repetition for Module 1 terminology"
    ]
  }
}
```

---

## progress.json

```json
{
  "studentId": "student-001",
  "currentModule": 2,
  "modules": {
    "module-1": {
      "status": "completed",
      "completedAt": "2026-03-29T01:00:00Z",
      "quizScore": 85,
      "quizAttempts": 1,
      "flashcardsCreated": 12,
      "notes": "Strong understanding of 5 Core Capabilities"
    },
    "module-2": {
      "status": "in_progress",
      "startedAt": "2026-03-29T02:00:00Z",
      "sectionsCompleted": ["2.1", "2.2"],
      "quizScore": null,
      "flashcardsCreated": 5
    },
    "module-3": { "status": "not_started" },
    "module-4": { "status": "not_started" },
    "module-5": { "status": "not_started" }
  },
  "totalTimeSpent": "1h 45m",
  "streak": 3,
  "lastSession": "2026-03-29T02:30:00Z"
}
```

---

## flashcards.json

```json
{
  "studentId": "student-001",
  "flashcards": [
    {
      "id": "fc-001",
      "module": "module-1",
      "front": "What are the 5 Core Capabilities of an AI Agent Framework?",
      "back": "1. Autonomous Execution\n2. Tool Use\n3. Memory\n4. Decision Making\n5. Action Chaining",
      "createdAt": "2026-03-29T01:00:00Z",
      "difficulty": "medium",
      "timesReviewed": 0,
      "timesCorrect": 0
    },
    {
      "id": "fc-002",
      "module": "module-1",
      "front": "What's the key difference between a chatbot and an AI agent?",
      "back": "Chatbots are reactive (respond to input), isolated (no memory), session-only. AI Agents are proactive, have persistent memory, can use tools, and chain actions autonomously.",
      "createdAt": "2026-03-29T01:05:00Z",
      "difficulty": "easy",
      "timesReviewed": 0,
      "timesCorrect": 0
    }
  ]
}
```

---

## reviews.json

```json
{
  "studentId": "student-001",
  "schedule": [
    {
      "flashcardId": "fc-001",
      "dueAt": "2026-03-30T01:00:00Z",
      "interval": 1,
      "easeFactor": 2.5,
      "nextReview": "2026-04-02T01:00:00Z"
    },
    {
      "flashcardId": "fc-002",
      "dueAt": "2026-03-30T01:00:00Z",
      "interval": 1,
      "easeFactor": 2.5,
      "nextReview": "2026-04-02T01:00:00Z"
    }
  ],
  "history": []
}
```

---

## Field Definitions

### discovery.learningStyle
| Value | Meaning |
|-------|---------|
| `visual` | Prefers diagrams, charts, sketchnotes |
| `reading` | Prefers written content, articles |
| `auditory` | Prefers discussion, verbal explanation |
| `hands_on` | Wants to build, code, tinker |
| `mixed` | Combination of above |

### discovery.timeAvailable
| Value | Meaning |
|-------|---------|
| `15min/day` | 15 minutes per day |
| `30min/day` | 30 minutes per day |
| `1hr/day` | 1 hour per day |
| `weekend` | Weekends only |
| `intensive` | Full-day sprints |

### discovery.priorKnowledge
| Value | Meaning |
|-------|---------|
| `complete_beginner` | No AI knowledge |
| `some_exposure` | Used ChatGPT or similar |
| `intermediate` | Built some prompts or automations |
| `advanced` | Building AI agents or systems |

### progress.modules[].status
| Value | Meaning |
|-------|---------|
| `not_started` | Not begun |
| `in_progress` | Started but not complete |
| `completed` | Finished with quiz passed |
| `needs_review` | Completed but review due |

---

*This schema is the source of truth for all student data.*
