---
name: date-batch
description: Generate four date ideas for the coming month. Engineered for variety — no two alike in energy, setting, or cost.
disable-model-invocation: false
user-invocable: true
---

## Quick Start

```
/date-batch                 → Four dates for this month
/date-batch [month]         → Plan ahead (e.g., /date-batch december)
```

**What you get:** A month-long date plan: 4 suggestions, each different in
character. Saved to `outputs/dates/`.

**Time:** 3-5 minutes.

---

## Pre-Flight: Context Check

Same as `/date-idea`. Read all context files before generating.
Check `memory/past-dates.md` — none of the 4 suggestions can appear there.

---

## Variety Matrix

The 4 suggestions must collectively satisfy this matrix:

| | Indoor | Outdoor |
|---|--------|---------|
| **Low effort** | ✓ required | |
| **Medium effort** | | |
| **Higher effort** | | ✓ required |

Also ensure:
- At least 1 is free or near-free
- At least 1 involves leaving home
- At least 1 could work on a weeknight
- No two suggestions are in the same category (food, culture, nature, creative, etc.)

---

## Output Format

```markdown
# Date Plan — [Month YYYY]

Four dates for the month ahead. Different energy, different settings. Use them in
any order — or save them for when the mood fits.

---

## Week 1: [Title]
**What:** [Description]
**Why now:** [Why it fits this time of year / their current context]
**Time:** [X hours] | **Cost:** [$ range] | **Works on:** [Weeknight / Weekend]

---

## Week 2: [Title]
**What:** [Description]
**Why now:** [Same]
**Time:** [X hours] | **Cost:** [$ range] | **Works on:** [Weeknight / Weekend]

---

## Week 3: [Title]
...

## Week 4: [Title]
...

---
*Run `/remember` after each one to log what worked.*
```

---

## Save Output

Save to: `outputs/dates/[YYYY-MM]-date-batch.md`
