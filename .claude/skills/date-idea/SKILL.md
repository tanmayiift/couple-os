---
name: date-idea
description: Generate a personalized date suggestion for this week or weekend. Always 1 primary + 2 alternatives.
disable-model-invocation: false
user-invocable: true
argument-hint: [optional: low-effort | splurge | outdoor | weekday name]
---

## Quick Start

```
/date-idea                  → Best fit for this week
/date-idea low-effort       → Minimal planning, low cost
/date-idea splurge          → Special occasion, higher budget OK
/date-idea outdoor          → Must involve outdoors/nature
/date-idea tuesday          → Optimized for a weeknight
```

## Context Files to Read
profile, preferences, financials, constraints, local-context, memory/past-dates, memory/learnings, memory/wishlist

## Workflow
1. Check flag from arguments. Check season, day of week.
2. Generate 6-8 candidates silently. Discard repeats, budget violations, bad fits.
3. Select 3: 1 primary + 2 alternatives at different effort levels.
4. Apply quality rules from `sub-agents/quality-rules.md`.

## Output Format

```
# Date Idea — [YYYY-MM-DD]

## This Week: [Title]

**What:** [2-3 sentences. Specific, visual, actionable.]
**Why it fits you:** [1-2 sentences citing their actual context.]
**Time needed:** [X hours]
**Approximate cost:** [specific range in their currency]
**Best day:** [recommendation]
**One thing to sort in advance:** [only if needed — skip if spontaneous]

---

## If That Doesn't Land

**Lower effort:** [Title] — [2 sentences. Cost and time.]
**Higher energy:** [Title] — [2 sentences. Cost and time.]

---
*Done this? Tell me how it went — or run /feedback for a quick debrief.*
```

## Save to
`outputs/dates/[YYYY-MM-DD]-date-idea.md`
