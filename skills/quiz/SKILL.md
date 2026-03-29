# Quiz Skill — Adaptive Knowledge Assessment

## Purpose

Generate adaptive quizzes that test student understanding of module content. Quizzes are tailored to the student's knowledge level, include multiple question types, and provide explanatory feedback.

---

## How It Works

### Question Types

| Type | Purpose | Example |
|------|---------|---------|
| **Recall** | Remember facts | "What are the 5 Core Capabilities?" |
| **Concept** | Understand principles | "Why is memory important in an AI agent?" |
| **Apply** | Use in new situations | "Which capability would you use to..." |
| **Analyze** | Break down scenarios | "This agent is failing because..." |

### Difficulty Levels

| Level | Trigger | Question Style |
|-------|---------|----------------|
| **Easy** | First quiz or struggling student | Direct recall, clear phrasing |
| **Medium** | Passing but room to grow | Concept + Apply questions |
| **Hard** | High performer, final assessment | Analyze + scenario-based |

Difficulty adjusts automatically based on the student's last quiz score:
- Score ≥ 80% → Next quiz: increase difficulty
- Score 60–79% → Keep difficulty same
- Score < 60% → Decrease difficulty + recommend review

---

## Quiz Generation Process

### Step 1: Load Module Content
```
Read: modules/module-[n]/CONTENT.md
```
Extract key concepts, terminology, and principles from the module.

### Step 2: Load Student Profile
```
Read: students/[student-id]/progress.json
```
Check quiz history, current module, and any flagged weak areas.

### Step 3: Generate Questions
Generate **5–10 questions** covering:
- 2–3 recall questions (always included)
- 2–3 concept questions
- 1–2 apply questions
- 1–2 analyze questions (if difficulty = hard)

Include:
- Clear question stem
- 4 answer options (for MCQ) or open-answer prompt
- Correct answer
- Explanation (why correct AND why distractors are wrong)
- Key concept the question maps to

### Step 4: Deliver Quiz
Present questions one at a time or as a set (based on session type):
- **Quick check:** 3 questions inline during module session
- **Full quiz:** 10 questions at end of module
- **Final assessment:** 25+ questions covering all modules

### Step 5: Score and Feedback
After submission:
1. Calculate score
2. Provide explanations for wrong answers
3. Flag weak concepts for flashcard creation
4. Update `students/[student-id]/progress.json`
5. If score < 60%, offer to revisit the module

---

## Output Format

Each quiz question follows this structure:

```
## Question [N]

**Type:** [Recall / Concept / Apply / Analyze]
**Difficulty:** [Easy / Medium / Hard]
**Module:** [Module N]
**Concept:** [Key concept being tested]

[Question text]

A) [Option A]
B) [Option B]
C) [Option C]
D) [Option D]

<details>
<summary>✅ Correct Answer</summary>

**[Letter]: [Answer text]**

**Explanation:** [Why this is correct and why others aren't]
</details>
```

---

## Special Quiz Types

### Quick Check (3 questions)
Inline during module delivery. Informal. No score recorded unless student requests it.

### Module Quiz (5–10 questions)
At the end of each module. Score recorded in `progress.json`. Required to "complete" a module.

### Comprehensive Final (25+ questions)
Covers all 5 modules. Required for certification. Includes scenario-based questions and a short open-answer section.

### Catch-Up Review Quiz
Adaptive quiz focusing only on previously failed or weak concepts. Generated before resuming a paused student.

---

## Flashcard Auto-Generation

After each quiz, automatically create flashcards for:
- Any concept the student got wrong
- Key terminology from the module
- Any "tricky" concepts the quiz flagged

Flashcards are saved to:
```
students/[student-id]/flashcards.json
```

Format per flashcard:
```json
{
  "id": "fc-auto-[number]",
  "module": "module-[n]",
  "front": "[Question]",
  "back": "[Answer]",
  "createdAt": "[timestamp]",
  "difficulty": "[easy/medium/hard]",
  "timesReviewed": 0,
  "timesCorrect": 0,
  "source": "quiz"
}
```

---

## Quiz Delivery Examples

### In-Text (Quick Check)
```
🧠 **Quick Check:**
After learning about the 5 Core Capabilities, which one do you think is 
the most important for a personal AI assistant? Why?
```

### Formal (End-of-Module)
```
📝 **Module 1 Quiz**

**1.** What are the 5 Core Capabilities of an AI Agent Framework?
   A) Memory, Tools, Decisions, Learning, Output
   B) Autonomous Execution, Tool Use, Memory, Decision Making, Action Chaining
   C) APIs, Webhooks, Context, Retrieval, Generation
   D) Planning, Execution, Review, Feedback, Optimisation

   ✅ B
   Explanation: The 5 Core Capabilities are specifically: Autonomous Execution,
   Tool Use, Memory, Decision Making, and Action Chaining. These define what
   makes an AI system "agentic" rather than just a chatbot.
```

---

## Quality Standards

- Every wrong answer includes an explanation (not just "incorrect")
- Questions are phrased clearly — no ambiguity
- Distractors (wrong answers) are plausible, not obviously wrong
- Quiz adapts to learning style if recorded in profile
- Quiz length respects the student's time availability setting

---

*Use this skill whenever you need to assess student understanding.*
