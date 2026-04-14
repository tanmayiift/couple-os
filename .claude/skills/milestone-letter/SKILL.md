---
name: milestone-letter
description: Claude writes a short letter in the couple's own voice about the period just passed — drawn from memory files and learnings. Something to keep.
user-invocable: true
argument-hint: [anniversary / after-trip / monthly / "describe the milestone"]
---

## Purpose

The highest emotional value command in this system.
A letter written from the couple's actual shared history — not a template,
not generic. Something that could only exist for them.

## Usage

```
/milestone-letter anniversary        → Annual letter for their anniversary
/milestone-letter after-trip         → Letter after returning from a trip
/milestone-letter monthly            → End of month reflection
/milestone-letter "one year"         → For a specific milestone you name
```

## Pre-Flight: Read Everything

Before writing a single word, read ALL of these from Notion (or local fallback):
- context-library/couple-profile.md — names, stage, how long together
- context-library/preferences.md — personality, environment, what they love
- context-library/memory/past-dates.md — every date logged
- context-library/memory/past-trips.md — every trip logged
- context-library/memory/learnings.md — everything discovered about them
- context-library/memory/memory-jar.md — the moments they've saved
- context-library/memory/wishlist.md — what they're still dreaming of

Check Notion first for each memory file. If Notion MCP is available, read from
Notion pages (they may contain entries from both partners). If not, fall back to
local markdown. Never mix sources mid-letter — use one or the other consistently.

This is not optional. The letter is only as good as the context you read.
If memory files are sparse, say so:
```
Your memory files are still fairly new — the letter will be short.
The more you log with /feedback and /memory-jar, 
the richer these letters become over time.
```

## Workflow

### Determine the period

- anniversary → "this past year"
- after-trip → "since [last trip in memory] to now"  
- monthly → "this past month"
- custom → use what they said

### Identify what happened in that period

Pull specific moments from memory files:
- Dates logged (especially highly rated ones)
- Trips taken
- Memory jar entries from this period
- Learnings added in this period
- Wishlist items that got crossed off

If nothing is logged for the period — say so and ask if they want to add
a few things first before the letter is written.

### Write the letter

Format:
```
[Month/Year or "One Year"]

[Partner 1 name] and [Partner 2 name],

[Body — 3-5 paragraphs. See tone rules below.]

[Closing line]
```

### Tone Rules

This is the hardest thing to get right. Read these carefully.

**Voice:** Write as if a close mutual friend who knows them well is writing TO them,
not as Claude. Warm but not saccharine. Specific but not clinical.

**What to include:**
- Specific things from their memory files — name the dates, trips, moments
- Small details that show you read their context ("the evenings you love on the terrace")
- Where they started vs where they are (use couple-profile.md + learnings.md)
- One thing from their wishlist still ahead of them — end with something to look forward to

**What never to include:**
- Generic relationship advice ("communication is key")
- Phrases like "your journey," "you've grown so much," "this chapter"
- Any sentence that could appear in a Hallmark card
- Anything that sounds like it was written by AI

**Length:** 250-400 words. Not longer. Letters should fit on one page.

**Test before outputting:** Read the letter back. Remove any sentence that 
could apply to a different couple. If more than 2 sentences are generic — rewrite.

### After writing

Save to:
- Notion Memory Jar page (create a "Letters" section if one doesn't exist, append)
- outputs/letters/[DATE]-[milestone-type]-letter.md

Display the letter, then say:
```
Saved to your memory jar. Run /milestone-letter [type] again next year —
it'll be longer.
```

Nothing else. Don't ask for feedback on the letter.
