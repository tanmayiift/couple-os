---
name: trip-idea
description: Generate a trip destination and concept. What to do, when to go, activity budget, why it fits. No hotels, no flights.
disable-model-invocation: false
user-invocable: true
argument-hint: [optional: weekend | week | long-haul | season | options]
---

## Quick Start

```
/trip-idea                  → Best fit given constraints
/trip-idea weekend          → 2-3 day trip
/trip-idea week             → 5-7 day trip
/trip-idea long-haul        → 10+ days
/trip-idea winter           → Season-specific
/trip-idea options          → 3 brief options instead of 1 deep-dive
```

## Context Files to Read
profile, preferences, financials, constraints, local-context, memory/past-trips, memory/wishlist, memory/learnings

## Anniversary & Milestone Detection

Before generating, check couple-profile.md for the wedding/anniversary date.

**Within 60 days of anniversary:**
- Suggest the trip as a potential anniversary trip. Frame timing accordingly.
- Pull from wishlist — international travel, adventure activities they've mentioned.

**Within 30 days:**
- Make it the primary angle: "Your [Nth] anniversary is [date] — here's a trip
  that fits the window."

**Relationship phase awareness:**
- Year 1: First international trip together as married. New territory, discovery.
- Year 2-3: Deeper, more immersive trips. Cooking classes, slow travel.
- Year 5+: Challenge trips. Trek, new continent, something they'd tell stories about.

**Also check:** sentiment patterns in learnings.md. If their best-rated
experiences lean `adventurous` or `new-discovery`, push the trip toward exploration.
If they lean `intimate` or `relaxing`, suggest slower-paced destinations.

## Scope
Covers: destination, activities, food culture, best time, activity budget, why it fits.
Does NOT cover: hotels, flights, restaurants by name, booking instructions.

## Output Format: Deep-Dive (Default)

```
# Trip Idea — [Destination]

## The Big Picture
[2-3 sentences — what and why, specific to this couple.]

## What You'd Actually Do There
**Day structure:** [Morning/afternoon/evening rhythm]
**Don't miss:** [5 activities, 1 sentence each]
**Food culture:** [2 sentences — what to eat, not where]

## Logistics Snapshot
**Trip length:** [duration] | **Best time:** [months] | **Activity budget:** [range] | **Effort to plan:** [Low/Med/High]

## Why This Fits You
[2-3 sentences citing their actual context. Must be impossible to write for a random couple.]

## One Thing to Know
[Honest flag: seasonal, booking, quirk, or expectation-setter.]
```

## Output Format: Options (with `options` flag)
3 brief options — 3 sentences each + trip length, budget, best time. End with: "Run /trip-idea [name] for a full breakdown."

## Save to
`outputs/trips/[YYYY-MM]-trip-idea.md`
