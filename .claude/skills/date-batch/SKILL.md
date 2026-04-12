---
name: date-batch
description: Generate four date ideas for the coming month. Engineered for variety — no two alike in energy, setting, or cost.
disable-model-invocation: false
user-invocable: true
argument-hint: [optional: month name]
---

## Quick Start

```
/date-batch                 → Four dates for this month
/date-batch december        → Plan ahead for a specific month
```

## Context Files to Read
profile, preferences, financials, constraints, local-context, memory/past-dates, memory/learnings

## Variety Rules
The 4 dates must collectively include:
- At least 1 indoor low-effort and 1 outdoor higher-effort
- At least 1 free or near-free
- At least 1 that works on a weeknight
- No two in the same category (food, culture, nature, creative, etc.)
- None in memory/past-dates.md

## Output Format

```
# Date Plan — [Month YYYY]

Four dates for the month. Different energy, different settings.

---

## Week 1: [Title]
**What:** [Description]
**Why now:** [Why this fits the time of year / their context]
**Time:** [X hours] | **Cost:** [range] | **Works on:** [Weeknight / Weekend]

## Week 2: [Title]
**What:** [Description]
**Why now:** [context]
**Time:** [X hours] | **Cost:** [range] | **Works on:** [Weeknight / Weekend]

## Week 3: [Title]
...

## Week 4: [Title]
...

---
*Run /feedback after each one to log what worked.*
```

## Save to
`outputs/dates/[YYYY-MM]-date-batch.md`
