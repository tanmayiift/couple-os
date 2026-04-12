---
name: trip-idea
description: Generate a trip destination and concept. What to do, when to go, activity budget, why it fits them. No hotels, no flights.
disable-model-invocation: false
user-invocable: true
---

## Quick Start

```
/trip-idea                  → Best fit given current constraints
/trip-idea weekend          → 2-3 day trip
/trip-idea week             → 5-7 day trip
/trip-idea long-haul        → 10+ days
/trip-idea winter           → Season-specific
/trip-idea options          → 3 brief options instead of 1 deep-dive
```

**What you get:** One destination deep-dive (or 3 brief options with `options` flag):
what to do there, best time to go, rough activity budget, and why it fits this couple.
No hotel or flight recommendations.

**Time:** 3-5 minutes.

---

## Scope Boundary (Critical)

This skill covers:
- ✅ Destination and why it fits this couple
- ✅ What to do there (activities, experiences, food culture, day structure)
- ✅ Best time of year to visit
- ✅ Rough activity/experience budget
- ✅ Length of trip recommendation
- ✅ What makes it different from other destinations

This skill does NOT cover:
- ❌ Hotel names or accommodation recommendations
- ❌ Flight routes or airlines
- ❌ Specific restaurant names (general food culture is fine)
- ❌ Booking instructions

If asked about hotels or flights: "That's intentionally outside what this system handles.
For accommodation and transport, I'd suggest [Booking.com / Skyscanner / similar] once
you've picked the destination."

---

## Pre-Flight: Context Check

Read:
1. `context-library/couple-profile.md` — Stage, kids, living situation
2. `context-library/preferences.md` — Activities, environment, energy
3. `context-library/financials.md` — Trip budget, trips per year
4. `context-library/constraints.md` — Leave available, notice needed, transport
5. `context-library/local-context.md` — Starting point, reachable destinations
6. `context-library/memory/past-trips.md` — Destinations already visited
7. `context-library/memory/wishlist.md` — Places they've mentioned wanting to visit

**If `past-trips.md` lists the destination you were going to suggest:** Pick a different one.
**If `local-context.md` doesn't have nearby cities:** Ask "What cities are within
a few hours of you?" before continuing.

---

## Workflow

### Step 1: Scope Assessment

From the command flag and context, determine:
- Trip length (weekend / week / long-haul)
- Budget ceiling for activities
- Season (from time of year or explicit flag)
- Starting geography (from local-context.md)
- Energy profile (from preferences.md)

### Step 2: Candidate Destinations

Generate 4-5 candidates silently. For each:
- Already in past-trips.md? Discard.
- Reachable given transport in constraints.md? If not, discard or flag.
- Does it match their activity energy level? If not, adjust or discard.
- Is it appropriate for their relationship stage (e.g., no honeymoon-level trips for
  someone dating 2 months unless that's their vibe)?

Select the strongest. For `options` flag, select 3.

### Step 3: Write Output

Deep-dive format unless `options` flag.

---

## Output Format: Deep-Dive (Default)

```markdown
# Trip Idea — [Destination Name]

## The Big Picture

[2-3 sentences on what this destination is and why it's the right pick for this couple.
Specific to their context — not a generic tourism pitch.]

---

## What You'd Actually Do There

**Day structure (typical):** [Morning / afternoon / evening rhythm — activities, not schedules]

**Don't miss:**
- [Activity 1 — 1 sentence with what makes it worth it]
- [Activity 2]
- [Activity 3]
- [Activity 4]
- [Activity 5]

**Food culture to explore:** [2 sentences — not restaurant names, but what to eat
and where to find it generally]

---

## Logistics Snapshot

**Trip length:** [Recommended duration]
**Best time to go:** [Month range and why — weather, crowds, cost]
**Activity budget:** [$ range for activities/experiences only, not accommodation/transport]
**Effort to plan:** [Low / Medium / High — how much research they'll need to do]

---

## Why This Fits You

[2-3 sentences that directly connect the destination to their specific preferences,
budget, stage, and wishlist. This section should be impossible to write for a
random couple — it must cite their actual context.]

---

## One Thing to Know

[One honest flag: seasonal consideration, booking-ahead requirement, a quirk about
the destination they should know, or something that makes it different from what
they might expect.]
```

---

## Output Format: Options (3 Brief)

```markdown
# Trip Options

Three directions, each a different character. Go deeper on whichever calls to you.

---

**Option 1: [Name]**
[3 sentences: what it is, what you'd do, why it fits them.]
Trip length: [X days] | Activity budget: [$ range] | Best time: [season]

---

**Option 2: [Name]**
...

**Option 3: [Name]**
...

---
*Run /trip-idea [destination name] to get a full breakdown on whichever interests you.*
```

---

## Save Output

Save to: `outputs/trips/[YYYY-MM]-trip-idea.md`
