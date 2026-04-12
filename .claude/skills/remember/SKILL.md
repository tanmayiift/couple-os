---
name: remember
description: Update context and memory files with new information or feedback.
disable-model-invocation: false
user-invocable: true
argument-hint: <what to remember>
---

## Quick Start

```
/remember we tried the hiking date, loved it
/remember partner hates loud restaurants
/remember we're moving to Bangalore in October
/remember we want to try pottery class
```

## Routing

| Signal | File | Format |
|--------|------|--------|
| Tried a date/activity + feedback | memory/past-dates.md | `\| date \| title \| rating \| note \|` |
| Completed a trip | memory/past-trips.md | `\| date \| dest \| duration \| rating \| note \|` |
| New preference | memory/learnings.md | `- [date]: observation` |
| Want to try something | memory/wishlist.md | `- [date]: item` |
| Life change | couple-profile.md or constraints.md | Update field |
| Budget change | financials.md | Update field |

## Rules
- Parse natural language. Map to correct file.
- Handle multiple updates in one message.
- If ambiguous, ask one clarifying question.
- If it contradicts existing context, flag it before overwriting.

## Confirmation
```
Got it. Updated `context-library/memory/[file]`:
→ [what was added]
```
