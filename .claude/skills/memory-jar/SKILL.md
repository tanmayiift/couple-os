---
name: memory-jar
description: A running log of favourite shared moments. Not dates — the small things worth keeping. Run /memory-jar read on bad days.
user-invocable: true
argument-hint: ["describe the moment" / read / read last]
---

## Purpose

Not functional. Not tracked for suggestions.
Just a place to put moments you want to keep.

The wrong turn in Jodhpur. The Sunday on the terrace.
The time it rained and you stayed in the car talking for an hour.
These don't need to be useful. They just need to exist somewhere.

## Usage

```
/memory-jar "the time we got lost in Jodhpur"     → Add a moment
/memory-jar read                                   → Read all memories
/memory-jar read last                              → Read the last 5
```

## Pre-Flight

Read couple-profile.md to get partner names. Use their real names if
you need to address them. Read from Notion Memory Jar page first; if
Notion MCP is unavailable, fall back to local memory-jar.md.

## Workflow: Adding a Memory

Parse $ARGUMENTS as the memory description.
If $ARGUMENTS is empty, ask: "What's the moment you want to remember?"

Then ask ONE follow-up only:
```
When was this, roughly? (doesn't need to be exact)
```

Format and save:

```markdown
---
**[DATE or "Around [month/year]"]**
[The memory, written in their own words with slight warmth added — 
not altered, just gently held. 2-4 sentences maximum.
If they wrote it in first person, keep it first person.
Don't editorialize. Don't add meaning they didn't give it.]
---
```

Save to:
- Notion Memory Jar page (append)
- context-library/memory/memory-jar.md (append)

Confirm with:
```
Added to your memory jar. You have [N] moments saved.
```

No further response. Don't analyse the memory. Don't comment on it.
Just confirm it's saved.

## Workflow: Read Mode

### /memory-jar read
Read all entries from Notion Memory Jar page / memory-jar.md.
Display them in reverse chronological order (newest first).
No commentary before or after. Just the memories.

### /memory-jar read last
Display only the 5 most recent entries.
Add at the end, quietly:
```
[N] total moments in your jar.
```

## Tone Rules for This Command

This is the most emotionally sensitive command in the system.
- Never psychoanalyse the memories
- Never add "what a lovely memory" or similar filler
- Never suggest what the memories mean
- Never connect them to suggestions or dates
- Write memory entries with warmth but no sentimentality
- If they're reading memories on a bad day, they don't need your commentary
  They just need to see the memories
