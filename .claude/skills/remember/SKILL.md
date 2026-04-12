---
name: remember
description: Update context and memory files when the couple shares new information or feedback.
disable-model-invocation: false
user-invocable: true
---

## Quick Start

```
/remember we tried the hiking date last weekend, loved it
/remember partner hates loud background music at restaurants
/remember we're planning to move to a new city in October
/remember we want to try a pottery class
/remember the Porto trip was amazing, would go back
```

**What you get:** Confirmation of exactly what was updated and where.

**Time:** Under a minute.

---

## How It Works

Parse the natural language input and determine:
1. What type of information is being shared
2. Which file to update
3. What format to add it in

Then update the file and confirm.

---

## Routing Logic

| What they said | File to update | Format |
|---------------|----------------|--------|
| Tried a date / activity, give feedback | `memory/past-dates.md` | Date, title, rating, note |
| Completed a trip | `memory/past-trips.md` | Destination, duration, rating, note |
| New preference discovered | `memory/learnings.md` | Free-form observation |
| New thing they want to try | `memory/wishlist.md` | Item with date added |
| Life change (move, job, kids) | `couple-profile.md` or `constraints.md` | Update relevant field |
| Budget change | `financials.md` | Update relevant field |

---

## Memory File Formats

### past-dates.md entry:
```
| [YYYY-MM-DD] | [Suggestion Title] | ❤️/👍/👎 | [Brief note] |
```

### past-trips.md entry:
```
| [YYYY-MM] | [Destination] | [Duration] | ❤️/👍/👎 | [Brief note] |
```

### learnings.md entry:
```
- [YYYY-MM-DD]: [Observation] (e.g., "Partner prefers smaller venues over large crowds")
```

### wishlist.md entry:
```
- [YYYY-MM-DD]: [Thing to try] (e.g., "Pottery class together")
```

---

## Confirmation Format

```
Got it. Updated `context-library/memory/[filename].md`:

→ [Exactly what was added, in one line]

[Optional: 1 sentence on how this affects future suggestions, if relevant]
```

---

## Edge Cases

**Ambiguous input:** If it's unclear which file to update, ask one specific question.
Don't guess.

**Multiple updates in one /remember:** Handle all of them. Confirm each one.

**Contradicts existing context:** Flag it.
"Noted — but this seems to contradict what's in `learnings.md`: [existing entry].
Should I update that too, or was the earlier note specific to a situation?"
