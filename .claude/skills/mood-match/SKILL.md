---
name: mood-match
description: Get a date suggestion calibrated to right now — energy level and mood, not just general preferences. The daily layer missing from /date-idea.
user-invocable: true
argument-hint: [optional: any context like "weeknight" or "2 hours max"]
---

## Purpose

Most date suggestions fail because they don't match the evening's energy.
/mood-match fixes this by asking two questions first, then suggesting
something calibrated to right now — not just general preferences.

## Workflow

### Step 1: Ask two questions only

Ask both questions at once, in one message. Do not ask separately.

```
Two quick questions before I suggest something:

1. Energy level right now — 1 (completely drained) to 5 (ready for anything)?

2. What kind of evening feels right?
   A) Adventurous — something new, a bit outside comfort zone
   B) Cosy — low effort, warm, familiar
   C) Social — people, energy, being out in the world
   D) Just us — quiet, private, no audience
```

Accept one-word or letter answers. Don't ask follow-ups.

### Step 2: Map to suggestion profile

| Energy | Mood | Suggestion Profile |
|--------|------|-------------------|
| 1-2 | Any | Home-based or within 15 min. Zero planning. |
| 3 | Cosy / Just us | Low-effort local. Familiar territory. |
| 3 | Adventurous / Social | Light version of something new. |
| 4-5 | Adventurous | Full /date-idea treatment, push the wishlist |
| 4-5 | Social | People, venues, energy |
| 4-5 | Just us | Intentional and special but private |

### Step 3: Read context

Read from Notion (or local fallback):
- couple-profile.md — use their actual names, relationship stage, city
- preferences.md — activity level, environment, personality types
- financials.md — date budget ranges and ceiling
- local-context.md — what's nearby in their city
- memory/past-dates.md — avoid repeats
- memory/learnings.md — apply known preferences
- memory/wishlist.md — pull from here for energy 4-5

Always use their names in the suggestion, not "you two" or "both of you."
Reference something specific from their context in the "why" line.

### Step 4: Generate suggestion

One suggestion only. No alternatives unless they ask.
Shorter format than /date-idea — this is a quick answer, not a full brief.

Format:
```
**[Suggestion Title]**

[2-3 sentences. What it is, what it looks like tonight.]

Time: [X hours] | Cost: [$ range]
[One sentence: why this fits their energy/mood right now]
```

Do not explain your reasoning at length. 
Do not offer three options unless explicitly asked.
Get to the suggestion fast — this command is for decisive evenings.

### Step 5: Save to Notion and local

Append to Past Dates page / past-dates.md:
```
| [DATE] | mood-match: [title] | [energy]/5, [mood type] | pending feedback |
```

Also append to `outputs/suggestion-log.md`:
```
| [DATE] | /mood-match | [title] | [category tag] | [indoor/outdoor] | suggested |
```

## Quality Check

Before outputting: would this suggestion make sense at [their stated energy level]
right now, tonight? If a 1-energy couple would need to drive 45 minutes — reject it.
