# Curriculum Generation Skill — Personalised Learning Paths

## Purpose

Transform the standard 5-module curriculum into a *personalised* learning path tailored to each student's role, goals, experience level, time availability, and learning style.

---

## How It Works

### Inputs

| Input | Source |
|-------|--------|
| Student discovery answers | `students/[id]/profile.json` → `discovery` |
| Student progress | `students/[id]/progress.json` |
| Standard curriculum | `modules/module-[n]/CONTENT.md` |
| Module durations | AGENTS.md |

### Process

```
Discovery Answers
       ↓
┌─────────────────────────────────────────┐
│  1. Assess experience level             │
│  2. Identify goals & context            │
│  3. Map goals → relevant modules       │
│  4. Adjust depth per module             │
│  5. Select relevant projects            │
│  6. Generate personalisation notes      │
│  7. Create time allocation plan         │
└─────────────────────────────────────────┘
       ↓
Personalised Curriculum Document
```

---

## Personalisation Rules

### 1. Experience Level Adjustment

| Level | Module 1-2 Depth | Module 3 Depth | Module 4 Depth |
|-------|-----------------|----------------|----------------|
| **Complete Beginner** | Full depth, extra analogies, no jargon | Full depth + prerequisites | Full depth |
| **Some Exposure** | Skip basics, focus on agentic distinction | Full depth | Full depth |
| **Intermediate** | Quick review, focus on gaps | Full depth, faster pace | Skip basics |
| **Advanced** | Skip or audit, fast-track to Modules 3-5 | Focus on architecture deep-dives | Skip ethics basics |

### 2. Goal-Based Module Emphasis

| Goal | Emphasise | De-emphasise |
|------|-----------|-------------|
| Career in AI | All modules, add coding content | — |
| Apply AI to current job | Modules 1, 2, 4 | Module 3 deep technical |
| Start AI side hustle | Modules 1, 2, 4, 5 | Module 3 (light) |
| Build AI products | All modules + project work | — |
| Just curious | Modules 1, 4, 5 (light) | Modules 2, 3 deep technical |

### 3. Learning Style Adaptation

| Style | Content Format | Quiz Style | Session Type |
|-------|---------------|-----------|-------------|
| **Visual** | Diagrams, ASCII art, sketchnotes | Image-based questions | Shorter, visual focus |
| **Reading** | Long-form text, detailed explanations | Written answers | Longer sessions |
| **Auditory** | Socratic dialogue, discussions | Verbal explanations | Conversational |
| **Hands-on** | Projects, code, builds | Practical challenges | Workshop-style |
| **Mixed** | Balanced mix | Flexible | Varies per session |

### 4. Time Availability Planning

| Availability | Session Length | Frequency | Est. Completion |
|-------------|---------------|-----------|----------------|
| `15min/day` | 2 × 15-min micro-sessions/week | 2/week | ~10 weeks |
| `30min/day` | 1 × 30-min session/week | 1/week | ~7 weeks |
| `1hr/day` | 1 × 1-hr session/week | 1/week | ~5 weeks |
| `weekend` | 1 × 3-hr session/weekend | 1/week | ~5 weeks |
| `intensive` | Multiple sessions/week | 3–4/week | ~2–3 weeks |

---

## Output: Personalised Curriculum Document

Generate a document with these sections:

```markdown
# Your Personalised AI Upskill Curriculum

**Student:** [Name]
**Generated:** [Date]
**Based on your goals:** [Goal summary]

## Your Learning Path

| Week | Module | Est. Time | Focus Areas |
|------|--------|-----------|-------------|
| 1 | Module 1 | 45 min | [Personalised focus] |
| 2 | Module 2 | 45 min | [Personalised focus] |
| ... | ... | ... | ... |

## Why This Path?

[3–5 sentences explaining how the curriculum was shaped 
by their role, goals, and experience level]

## Key Differences from Standard Path

- [Customisation 1]
- [Customisation 2]
- ...

## Recommended Mini-Projects

From Module 5 projects, recommend 2–3 most relevant to their goals.

## Your First Session

[Specific preview of Module 1, personalised with their context]

## Notes

[Any special considerations: time constraints, prior knowledge gaps, etc.]
```

Save as:
```
students/[student-id]/curriculum.md
```

---

## Curriculum Update Triggers

Regenerate or update the curriculum when:

| Trigger | Action |
|---------|--------|
| New student | Generate full personalised curriculum |
| Student completes a module | Review and confirm next module focus |
| Student struggles (quiz < 60%) | Regenerate with more foundational focus |
| Student requests change | Regenerate with updated preferences |
| 30+ days since last session | Review and refresh curriculum |

---

## Content Depth Levels

### Light (30% of standard time)
- Core concepts only
- Key terminology
- 1 practical example
- Quick 3-question quiz

### Standard (100% of standard time)
- Full content coverage
- All examples
- Full quiz
- Flashcards generated

### Deep (150% of standard time)
- Full content + advanced concepts
- Additional research questions
- Complex project work
- Extended quiz + peer discussion

---

## Multi-Student Support

Each student gets their own `curriculum.md` in their directory:
```
students/student-001/curriculum.md
students/student-002/curriculum.md
...
```

---

*Use this skill when starting with a new student or when a curriculum review is needed.*
