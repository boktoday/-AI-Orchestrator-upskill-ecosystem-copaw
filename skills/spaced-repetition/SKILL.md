# Spaced Repetition Skill — Long-Term Memory Retention

## Purpose

Use proven spaced repetition science to ensure students retain what they learn. Key concepts are turned into flashcards, and review sessions are scheduled at optimal intervals to maximise long-term retention with minimum effort.

---

## The Science

Spaced repetition works because it aligns with how human memory decays:

```
Retention

100% |  *
     |    *
 80% |      *-------
     |             *-------
 60% |                  *--------
     |                          *------
 40% |                                *-------
     |                                       *----
 20% |                                             *--
   0% +----+----+----+----+----+----+----+----+-----> Time
        1d   3d   7d   14d  30d  60d  90d

Without review: Memory fades fast
With spaced review: Each session strengthens long-term memory
```

**The SM-2 Algorithm** (simplified):
- After each review, adjust the interval based on performance
- Correct answers → interval increases (you know it!)
- Wrong answers → interval resets (needs more work)

---

## Flashcard Creation

### Trigger Points

Flashcards are created automatically at these points:

| Event | Action |
|-------|--------|
| Module content delivery | Extract key concepts → create 5–10 flashcards |
| Quiz completion | Convert wrong answers → flashcard with explanation |
| Key term introduced | Create term-definition flashcard |
| Student struggle | Create targeted flashcard for weak area |

### Flashcard Structure

```json
{
  "id": "fc-auto-001",
  "module": "module-1",
  "front": "What makes an AI system 'agentic'?",
  "back": "An AI system is 'agentic' when it can:\n1. Execute tasks autonomously\n2. Use tools\n3. Maintain memory\n4. Make decisions\n5. Chain actions together\n\nvs. a chatbot which only responds to input.",
  "createdAt": "2026-03-29T10:00:00Z",
  "tags": ["core-concept", "terminology"],
  "difficulty": "medium",
  "source": "content",
  "timesReviewed": 0,
  "timesCorrect": 0,
  "easeFactor": 2.5,
  "interval": 1,
  "nextReview": "2026-03-30T10:00:00Z"
}
```

---

## Spaced Repetition Schedule

### Standard Review Schedule

| Review | Timing | Trigger |
|--------|--------|---------|
| **1st Review** | 1 day after learning | Fresh memory → consolidate |
| **2nd Review** | 3 days after 1st | Catch what started fading |
| **3rd Review** | 7 days after 2nd | Strengthen for medium-term |
| **4th Review** | 14 days after 3rd | Build long-term retention |
| **5th Review** | 30 days after 4th | Lock it in permanently |

### SM-2 Interval Calculation

```
After review:
- If CORRECT (quality ≥ 3):
  - If first review: interval = 1 day
  - If second review: interval = 3 days
  - Otherwise: interval = previous_interval × easeFactor
  - easeFactor = max(1.3, easeFactor + 0.1)
  
- If WRONG (quality < 3):
  - interval = 1 day
  - easeFactor = max(1.3, easeFactor - 0.2)
  - Reset streak
```

### Quality Ratings

| Rating | Meaning |
|--------|---------|
| 0 | Complete blackout — no recall |
| 1 | Wrong, but remembered after seeing answer |
| 2 | Wrong, but answer seemed easy to recall |
| 3 | Correct, with significant difficulty |
| 4 | Correct, with some hesitation |
| 5 | Perfect — instant recall |

---

## Review Session Format

### Start of Each Session

1. Check `students/[id]/reviews.json` for cards due today
2. If due cards exist → run review session first
3. If no due cards → proceed directly to new content

### Review Session Structure

```
🧠 **Flashcard Review** — [N] cards due today

---

**Card 1 of [N]**

**Module:** Module 1 — The Agentic Revolution
**Times reviewed:** 2 | **Last result:** ✅ Correct

---

What are the 5 Core Capabilities of an AI Agent Framework?

[Type your answer, then reveal:]

✅ **Answer:**
1. Autonomous Execution
2. Tool Use
3. Memory
4. Decision Making
5. Action Chaining

---

**How did that feel?**
- 😅 Blackout (0)
- 🤔 Struggled (1-2)
- 💪 Got it! (3-5)

---

**Next card →**
```

### End of Review Session

1. Save updated review data to `students/[id]/reviews.json`
2. Schedule next review dates using CoPaw cron skill
3. If many wrong answers → flag module for revisit
4. Celebrate consistency (streak tracking)

---

## CoPaw Cron Integration

Use the **CoPaw cron skill** to automatically schedule review reminders:

```bash
# After creating flashcards, schedule reviews:
copaw cron create \
  --agent-id [your-agent-id] \
  --name "Review: [student-id] flashcards" \
  --schedule "2026-03-30T10:00:00Z" \
  --payload "review_session:[student-id]"
```

The cron job triggers a review reminder message to the student.

### Review Reminder Message Template

```
📚 **[student-name], your flashcards are ready!**

You have [N] flashcards due for review.
Estimated time: [N] minutes

Topics:
- Module 1: 3 cards
- Module 2: 2 cards
...

Reply "Review" to start, or "Skip" to postpone to tomorrow.
```

---

## Storage Schema

### flashcards.json
```json
{
  "studentId": "student-001",
  "flashcards": [ ... ],
  "totalCards": 47,
  "masteredCards": 12,
  "learningCards": 23,
  "newCards": 12
}
```

### reviews.json
```json
{
  "studentId": "student-001",
  "schedule": [ ... ],
  "history": [
    {
      "date": "2026-03-29T10:00:00Z",
      "cardsReviewed": 10,
      "cardsCorrect": 8,
      "sessionDuration": "5min"
    }
  ],
  "currentStreak": 3,
  "longestStreak": 7
}
```

---

## Mastery Thresholds

| Status | Criteria |
|--------|---------|
| **New** | Never reviewed |
| **Learning** | Reviewed < 3 times OR easeFactor < 2.0 |
| **Reviewing** | Reviewed ≥ 3 times, easeFactor 2.0–2.5 |
| **Mastered** | Reviewed ≥ 5 times, easeFactor ≥ 2.5, interval ≥ 30 days |

---

## Edge Cases

| Situation | Action |
|-----------|--------|
| No cards due | Skip review, proceed to new content |
| Student skips 3+ reviews | Send gentle re-engagement message |
| All cards mastered | Suggest module extension or new content |
| Student gets 80%+ correct first time | Flag as "fast learner" → suggest harder content |
| Student gets < 50% correct | Flag for curriculum review + suggest module reread |

---

*Use this skill at the start of every session to run flashcard reviews.*
*Use the CoPaw cron skill to schedule future review reminders automatically.*
