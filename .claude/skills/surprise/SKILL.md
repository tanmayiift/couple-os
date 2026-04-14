---
name: surprise
description: One partner plans a surprise for the other. Reads the recipient's individual preferences and generates something calibrated specifically for them. Never syncs to Notion — stays local only.
user-invocable: true
argument-hint: [partner name from couple-profile.md]
---

## Purpose

Sometimes a date isn't about "us" — it's about one partner doing something
intentional for the other. /surprise generates a plan calibrated to the
recipient's individual tastes, with the planner as the supporting role.

## CRITICAL: No Notion Sync

This command NEVER writes to Notion. Ever. The whole point is that the
other partner doesn't see it coming.

Save only to: `outputs/surprises/[YYYY-MM-DD]-surprise-[recipient].md`
Do NOT update past-dates.md, learnings.md, or any shared memory file.
Do NOT mention the surprise in any Notion page.

After the surprise happens, the couple can log it normally with /feedback.

## Usage

```
/surprise [partner name]  → Plan something for that partner
/surprise                 → Ask who it's for
```

## Pre-Flight: Deep Context Read

Read ALL of these — you need the full picture of the recipient:

- couple-profile.md — names, relationship stage, anniversary date
- preferences.md — FOCUS on the recipient's individual preferences:
  - Their personality type (introvert/extrovert/ambivert)
  - Their specific interests (art, music, dance vs sports)
  - Their energy patterns (morning vs evening person)
  - Their comfort zones and boundaries
- financials.md — budget (surprises can stretch to splurge ceiling)
- constraints.md — scheduling, transport
- local-context.md — what's nearby, what they already love
- memory/past-dates.md — what's been done (avoid repeats)
- memory/learnings.md — discovered preferences about the recipient
- memory/wishlist.md — things the recipient has mentioned wanting

## Partner Profiles (Pull from Context, Don't Hardcode)

Read preferences.md carefully and build a mental model of each partner:

**When planning for Partner 1 (check couple-profile.md for name):**
- Pull their personality, interests, energy level from preferences.md
- Check learnings.md for anything they specifically loved or reacted to
- Check wishlist.md for things they've expressed interest in

**When planning for Partner 2:**
- Same process, different lens
- Pay special attention to comfort boundaries (social settings, activity types)

## Workflow

### Step 1: Identify recipient

Parse $ARGUMENTS for a name. Match against couple-profile.md.
If no name given, ask: "Who's the surprise for?"

### Step 2: Ask the planner 3 questions

```
Planning a surprise for [recipient name]. Quick questions for you:

1. What's the occasion? (Just because / Anniversary / Birthday / 
   Rough week / They've been wanting this)

2. How much effort can you put into setup?
   A) Zero — I need something I can pull off tonight
   B) A few days to arrange something
   C) I'm willing to plan properly for this one

3. Any constraints tonight/this week I should know about?
```

### Step 3: Generate the surprise

Build a plan that leans into the **recipient's** preferences, not the couple average.

The suggestion must:
- Reference at least 2 specific things about the recipient from context files
- Match the recipient's energy type (not the planner's)
- Fit within the stated occasion and effort level
- Include specific details the planner can act on

Format:
```markdown
# Surprise for [Recipient Name] — [YYYY-MM-DD]

## The Plan: [Title]

**What you're doing:** [3-4 sentences. Specific, actionable, visual. 
Written TO the planner — "you" = the planner, "[recipient]" = recipient.]

**Why [recipient] will love this:** [2 sentences citing specific things 
about them — their interests, something from learnings, a wishlist item, 
their personality type.]

**Setup checklist:**
- [ ] [Specific thing to arrange]
- [ ] [Specific thing to buy/prepare]  
- [ ] [Specific timing to hit]

**Time:** [X hours]
**Cost:** [₹ range]
**Best moment to reveal:** [When to tell them / when to start]

## If You Need a Backup

**Simpler version:** [2 sentences — same vibe, less setup]

---
*After the surprise, run /feedback to log it — that's when it enters shared memory.*
```

### Step 4: Save locally only

Save to: `outputs/surprises/[YYYY-MM-DD]-surprise-[recipient-name].md`

Create the `outputs/surprises/` directory if it doesn't exist.

NEVER:
- Write to Notion
- Update past-dates.md
- Update any shared memory file
- Mention the surprise in any subsequent command output

### Quality Checks

Before outputting:
- [ ] Would the RECIPIENT (not the planner) enjoy this? Check against their specific preferences.
- [ ] Is this different from what the couple normally does together? A surprise should feel different.
- [ ] Does the "why they'll love this" cite real context about the recipient specifically?
- [ ] Is the setup checklist actionable enough that the planner can actually execute?
- [ ] Did you accidentally reference the planner's interests instead of the recipient's?

## Tone

Write to the planner like a co-conspirator. Direct, practical, a little excited.
Not sappy. Not generic. Make them feel like they have an unfair advantage
because they know exactly what their partner loves.
