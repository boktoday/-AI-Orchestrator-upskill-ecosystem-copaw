# AI Orchestrator Upskill — CoPaw Edition

> A complete AI learning orchestration system built for CoPaw agents.

![Platform](https://img.shields.io/badge/Platform-CoPaw-blue)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 🎯 What Is This?

A multi-agent AI learning system that:

1. **Discovers** who the student is (role, goals, experience, learning style)
2. **Generates** a personalised curriculum from 5 core modules
3. **Delivers** interactive, adaptive learning sessions
4. **Retains** knowledge using spaced repetition
5. **Certifies** students with quizzes, projects, and an action plan

---

## 🧠 The 5-Module Curriculum

| # | Module | Duration | What You Learn |
|---|--------|----------|----------------|
| 1 | The Agentic Revolution | 45 min | AI Agents vs Chatbots, 5 Core Capabilities |
| 2 | The Tech Stack of 2026 | 45 min | LLMs, APIs, Webhooks, AI Tooling |
| 3 | Deep Dive into AI Orchestration | 60 min | Agent Architecture, Memory, Skills, Tools |
| 4 | Strategy & Practical Application | 30 min | AI Strategy, Ethics, ROI, Use Cases |
| 5 | Knowledge Check & Practice | Variable | Quizzes, Projects, Final Assessment |

---

## 🏗️ Architecture

```
AI-Orchestrator-Upskill-CoPaw/
├── SOUL.md                          ← Agent identity & philosophy
├── AGENTS.md                        ← Orchestrator workflow
├── SCHEMA.md                        ← Student data schema
├── STUDENT.md                       ← Student onboarding template
├── README.md                        ← This file
│
├── modules/                         ← Course content (5 modules)
│   ├── module-1/CONTENT.md
│   ├── module-2/CONTENT.md
│   ├── module-3/CONTENT.md
│   ├── module-4/CONTENT.md
│   └── module-5/
│       ├── CONTENT.md               ← Final assessment content
│       └── PROJECTS.md              ← Mini-projects
│
├── skills/
│   ├── quiz/SKILL.md               ← Adaptive quiz generation
│   ├── curriculum/SKILL.md         ← Curriculum personalisation
│   └── spaced-repetition/SKILL.md ← Flashcard & review system
│
├── students/                        ← Per-student data
│   └── [student-id]/
│       ├── profile.json
│       ├── progress.json
│       ├── flashcards.json
│       └── reviews.json
│
└── images/                          ← Sketchnotes & visuals
```

---

## ⚙️ CoPaw Skills Used

| Skill | Role |
|-------|------|
| `skills/quiz/SKILL.md` | Generates adaptive MCQ & open-answer quizzes |
| `skills/curriculum/SKILL.md` | Personalises curriculum per student profile |
| `skills/spaced-repetition/SKILL.md` | Flashcards + review scheduling |
| CoPaw `cron` skill | Schedules future review reminders |
| CoPaw `multi_agent_collaboration` | Spawns module-specific sub-agents |
| CoPaw `docx` skill | Generates certificates of completion |

---

## 🚀 How to Run

### 1. Load the Orchestrator
Give this workspace to your CoPaw agent, or copy the `AI-Orchestrator-Upskill-CoPaw/` folder into your CoPaw workspace.

### 2. Start a New Student
The orchestrator handles everything. Just say:
> "I'm new. I want to learn about AI agents."

The orchestrator will:
- Ask discovery questions
- Generate a personalised curriculum
- Begin Module 1

### 3. Continue a Student
Say:
> "Continue with student-001"

The orchestrator loads the profile and resumes from where they left off.

---

## 📋 Student Data Schema

See `SCHEMA.md` for the full JSON schema used to track student profiles, progress, and reviews.

---

## 🏆 Certification

After completing all 5 modules, students receive:
- ✅ Comprehensive knowledge check
- ✅ Mini-project submission
- 📄 Personal AI Action Plan
- 🎓 Certificate of Completion (generated via `docx` skill)

---

## 👨‍🏫 For Instructors

To onboard a new student:
1. Say "New student" to the orchestrator
2. The orchestrator runs discovery
3. A `students/student-[n]/profile.json` is created automatically
4. Modules are tracked automatically

---

## 🔧 Customisation

- **Add modules:** Create `modules/module-6/NAME/CONTENT.md` and update `AGENTS.md`
- **Change quiz style:** Edit `skills/quiz/SKILL.md`
- **Adjust spaced repetition:** Edit `skills/spaced-repetition/SKILL.md`
- **Regenerate curriculum logic:** Edit `skills/curriculum/SKILL.md`

---

## 📄 License

MIT — Built by [@boktoday](https://github.com/boktoday) · Powered by CoPaw
