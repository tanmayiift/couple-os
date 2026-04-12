---
name: activity-pack
description: Generate five non-date shared activities: hobbies to try, rituals to build, creative projects, traditions to establish.
disable-model-invocation: false
user-invocable: true
---

## Quick Start

```
/activity-pack              → Five activities, varied mix
/activity-pack hobbies      → Focus on new shared hobbies
/activity-pack rituals      → Focus on recurring weekly/monthly rituals
/activity-pack creative     → Creative projects to do together
```

**What you get:** Five distinct shared activities at different time and cost levels.
Mix of one-time experiences and recurring habits.

**Time:** 2-3 minutes.

---

## What This Is (and Isn't)

Activity Pack is for the space between dates. It's about building a richer shared
life — not just planning evenings, but finding things to do together that become
part of how the couple operates.

**Categories to draw from:**
- New shared hobbies (pottery, climbing, language learning, cooking a cuisine)
- Recurring rituals (Sunday routine, monthly tradition, seasonal habit)
- Creative projects (something they make together — not just consume)
- Physical activities (not as an obligation, as an anchor)
- Cultural habits (something they learn or explore together over time)

**Not this:** Date night suggestions. Those belong in /date-idea.

---

## Pre-Flight: Context Check

Read:
1. `context-library/preferences.md` — Activity level, interests, environment preference
2. `context-library/constraints.md` — Time availability, transport, mobility
3. `context-library/memory/learnings.md` — Known interests and preferences
4. `context-library/memory/wishlist.md` — Things they've said they want to try

---

## Output Format

```markdown
# Activity Pack — [Month YYYY]

Five things to add to your life together. Some are one-offs, some are habits.
Pick one to start this week.

---

### 1. [Activity Title]
**What it is:** [2-3 sentences. Specific enough to act on.]
**Why it fits you:** [1 sentence connecting to their context]
**Time commitment:** [One-time / Weekly / Monthly — and how long each session]
**Cost to start:** [$ range]
**How to start:** [One specific first step — what to search, buy, sign up for, or do]

---

### 2. [Activity Title]
...

### 3. [Activity Title]
...

### 4. [Activity Title]
...

### 5. [Activity Title]
...

---
*Use /remember to log which ones you try and whether they stuck.*
```

---

## Variety Rules

Across the 5 suggestions:
- At least 1 recurring ritual (not one-off)
- At least 1 creative or making-something activity
- At least 1 can start this week with zero lead time
- At least 1 involves leaving the house
- No two in the same category

---

## Save Output

Save to: `outputs/activities/[YYYY-MM]-activity-pack.md`
