---
name: activity-pack
description: Five non-date shared activities — hobbies, rituals, creative projects, traditions.
disable-model-invocation: false
user-invocable: true
argument-hint: [optional: hobbies | rituals | creative]
---

## Quick Start

```
/activity-pack              → Five activities, varied mix
/activity-pack hobbies      → Focus on new shared hobbies
/activity-pack rituals      → Focus on recurring rituals
/activity-pack creative     → Creative projects together
```

## Context Files to Read
couple-profile, preferences, constraints, memory/learnings, memory/wishlist

## Variety Rules
- At least 1 recurring ritual (not one-off)
- At least 1 creative/making-something activity
- At least 1 starts this week with zero lead time
- At least 1 involves leaving the house
- No two in the same category

## Output Format

```
# Activity Pack — [Month YYYY]

Five things to add to your life together. Pick one to start this week.

---

### 1. [Title]
**What it is:** [2-3 sentences]
**Why it fits you:** [1 sentence from context]
**Time commitment:** [One-time / Weekly / Monthly — duration per session]
**Cost to start:** [range]
**How to start:** [One specific first step]

### 2-5. [Same format]

---
*Use /feedback to log which ones stuck.*
```

## Save to
`outputs/activities/[YYYY-MM]-activity-pack.md`
