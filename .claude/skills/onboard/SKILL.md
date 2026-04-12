---
name: onboard
description: Quick-start intake that learns who you are as a couple. 5-7 minutes, three rounds, then your first date idea on the spot.
disable-model-invocation: false
user-invocable: true
argument-hint: [optional: update]
---

## Quick Start

```
/onboard               → First-time setup (5-7 min)
/onboard update        → Update after a life change
```

## Context Files to Read
Check if `context-library/couple-profile.md` exists with real data. If yes, offer: start fresh or update what's changed.

## How It Works

Three conversational rounds. Not a form. Ask in batches, never number questions.
Only ask things only they would know. Geography, climate, airports, nearby cities — figure those out yourself from their city.

**Round 1 — Who are you two?**
One open prompt: names, city, how long together, dating/married, living situation, kids.
Save to `context-library/couple-profile.md`. Auto-populate `context-library/local-context.md` geography from their city.

**Round 2 — What makes you tick?**
What they enjoy together, wishlist, clear misses, energy level, food (veg/non-veg/allergies), morning vs night, introvert vs extrovert.
Save to `context-library/preferences.md`. Give a quick observation that proves you listened.

**Round 3 — Logistics and money**
Date budget range, trip budget approach, work schedules, weekend availability, transport, local spots they love, places to avoid.
Save to `context-library/financials.md`, `context-library/constraints.md`, update local-context.md with their personal spots.

**Finish with impact:** Generate a full `/date-idea` output immediately — primary + 2 alternatives. This is the proof onboarding worked.

## Rules
- Under 7 minutes total. Three rounds max.
- Never say "Great answers!" — just move forward.
- The final date idea is mandatory. Don't end with a summary.
