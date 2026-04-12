---
name: week-ritual
description: Suggest one small recurring weekly ritual tailored to this couple.
disable-model-invocation: false
user-invocable: true
---

## Quick Start

```
/week-ritual                → One ritual suggestion
```

## Context Files to Read
preferences, constraints, memory/learnings. Also check outputs/activities/rituals.md if it exists (avoid repeats — this file won't exist until the first ritual is generated).

## What a Ritual Is
- Recurring (weekly or set rhythm)
- Small (20 min to 2 hours)
- Anchored to a time or trigger
- Specific to this couple (not generic)

NOT a date idea. NOT a one-off. NOT something requiring planning each time.

## Output Format

```
## [Ritual Title]

**The ritual:** [2-3 sentences. What, when, what it looks like in practice.]
**Why it fits you:** [1 sentence from their context.]
**When to anchor it:** [Specific time — "Sunday morning before noon"]
**What you need:** [Minimal list — or "nothing"]
**How to start:** [One action to do this week]
```

## Save to
Append to `outputs/activities/rituals.md` (create if it doesn't exist; don't overwrite — this file accumulates).
