---
name: feedback
description: Quick debrief after a date, trip, or activity. Three questions, under 2 minutes, auto-updates memory.
disable-model-invocation: false
user-invocable: true
argument-hint: [optional: what you did]
---

## Quick Start

```
/feedback                          → Start a debrief
/feedback hiking date last weekend → Skip Q1, jump to rating
```

**What you get:** Memory files updated. Future suggestions reflect what worked and what didn't.

**Time:** Under 2 minutes.

---

## Workflow

If an argument was provided (e.g., "hiking date last weekend"), use it as the answer
to Q1 and skip straight to Q2.

Otherwise, ask exactly these three questions in order. Accept short answers.

**Q1:** "What was it? (the date, trip, or activity — name or describe it briefly)"

**Q2:** "How did it go?"
Accept natural language. Map to rating internally:
- Loved it / amazing / best ever → ❤️
- Good / solid / enjoyed it → 👍
- Meh / mixed / okay → 👍 with a note
- Bad / miss / didn't work → 👎

**Q3:** "One thing worth remembering for next time?"
This is the learning. Accept anything: "venue was too loud," "the sunset timing
was perfect," "skip the appetizers," "do this again in winter."

---

## After Collecting Answers

Update the right files:

1. **If it was a date or activity:** Add entry to `context-library/memory/past-dates.md`
   Format: `| [YYYY-MM-DD] | [Title] | [❤️/👍/👎] | [Note from Q3] |`

2. **If it was a trip:** Add entry to `context-library/memory/past-trips.md`
   Format: `| [YYYY-MM] | [Destination] | [Duration] | [❤️/👍/👎] | [Note] |`

3. **If Q3 contains a preference signal:** Also add to `context-library/memory/learnings.md`
   Format: `- [YYYY-MM-DD]: [Observation]`

---

## Confirmation

```
Got it. Updated [files changed]:
→ [what was logged, one line]

[If a learning was extracted:] Also noted: "[learning]" — this'll shape future suggestions.
```

No follow-up questions. Keep it fast. Done.
