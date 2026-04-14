---
name: streak
description: Shows how many consecutive months the couple has logged a date + feedback. Celebrates the habit, not the streak number.
user-invocable: true
argument-hint: [check / history]
---

## Purpose

Small habit anchors matter more than big features.
/streak makes the feedback habit feel like something worth keeping.

Not a gamification system. Not points. Just: you showed up, and it counts.

## Usage

```
/streak           → Check current streak + celebrate if milestone
/streak history   → Show full monthly log
```

## Workflow: Check Mode (default)

### Step 1: Read streak data

Read couple-profile.md first — use their actual names in all output.
Read from Notion Streak page / context-library/memory/streak.md.
Read past-dates.md to verify the log independently.
For milestone messages, also read memory-jar.md for specific moments to reference.

### Step 2: Calculate streak

A month "counts" if both of these are true:
1. At least one date was logged (any entry in past-dates.md for that month)
2. At least one feedback rating was given (not "pending feedback")

Count consecutive months backward from the current month.
If this month has a logged + rated date: include it.
If this month has no entry yet: streak counts up to last month.

### Step 3: Determine milestone tier

| Streak | Milestone |
|--------|-----------|
| 1 month | First one. The hardest one. |
| 3 months | A quarter in. |
| 6 months | Half a year of showing up. |
| 12 months | A full year. |
| 18 months | Longer than most habits last. |
| 24 months | Two years. |

### Step 4: Output

For streaks with no milestone:
```
**[N] months in a row** of logging dates together.

Last logged: [date and suggestion title]
This month: [logged / not yet — run /feedback to keep it going]

Longest streak: [N] months
```

For milestone streaks (hitting 3, 6, 12, 18, 24):
```
**[N] months.**

[One specific sentence referencing something real from their logs —
a date they loved, a trip they took, something from memory-jar.md.
Make it specific to them. Not generic congratulations.]

Longest streak: [N] months
[N] dates logged total.
```

For a broken streak (gap month detected):
```
Streak reset. Last run was [N] months.

[One gentle, non-guilt sentence. Not motivational. Not judgemental.
Something like: "Life gets in the way. The jar is still here."]

Start a new one: log any date this month and rate it with /feedback.
```

### Step 5: Update streak file

Update context-library/memory/streak.md and Notion Streak page:
```markdown
Current streak: [N] months
Longest streak: [N] months  
Last logged: [DATE] — [suggestion title]

## Monthly Log
| [YYYY-MM] | [date title] | [rating] | ✓ counts |
```

## Tone Rules

- Never use the word "amazing" or "awesome"
- Never say "keep it up" or "you've got this"
- Milestone messages are quiet and specific — not congratulatory
- Broken streak messages are brief and without shame
- The habit is the reward. The streak is just a count.
