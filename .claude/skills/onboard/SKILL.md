---
name: onboard
description: Quick-start intake that learns who you are as a couple. 5-7 minutes, three rounds, then your first date idea on the spot.
disable-model-invocation: false
user-invocable: true
---

## Quick Start

```
/onboard               → First-time setup (5-7 min)
/onboard update        → Update after a life change
```

**What you get:** All context files populated. Then your first personalized date
idea generated immediately — so you see the payoff before you close the session.

**Time:** 5-7 minutes. Three rounds of conversation, not a form.

---

## Philosophy

This is not a questionnaire. It's a quick conversation. The couple should feel
like they're telling a friend about themselves, not filling out a government form.

Rules:
- **Ask in batches, not one at a time.** Group related questions so they can answer in one natural message.
- **Never number questions.** That makes it feel like a survey. Use conversational flow.
- **Extract, don't interrogate.** If they give you three things in one answer, don't re-ask the other two.
- **Show value fast.** After Round 2, generate a quick preview. After Round 3, generate a real date idea.
- **Never ask what you can figure out yourself.** If you know their city, YOU fill in nearby cities, airports, climate, day trip options, flight destinations. The couple should only answer things only they would know (preferences, budget, personal history).

---

## What to Ask vs. What to Figure Out Yourself

**ONLY ask the couple:**
- Names, relationship stage, how long together, living situation, kids
- What they enjoy, what they hate, what they want to try
- Food preferences, energy levels, personality
- Budget ranges, work schedules, transport, weekend availability
- Neighborhood they live in, local spots they already love, places to avoid

**NEVER ask the couple (figure these out from their city):**
- Nearby cities or day trip destinations
- Nearest airport
- Short-haul flight destinations
- Climate and seasons
- Character of the area (research it yourself)
- General geography or travel logistics from their location

You are a language model. You know geography. Use it.

---

## Pre-Run Check

If context files already have data:

```
You've already got context filled in. Want to:
1. Start fresh
2. Just update what's changed

Which one?
```

If empty, jump straight in with the hook.

---

## The Hook (First Message)

Start with energy, not instructions:

```
Let's get you set up. Three quick rounds — takes about 5 minutes — and
then I'll generate your first date idea on the spot so you can see how this works.

Round 1: Who are you two?

Tell me the basics — what should I call you, where do you live, how long
you've been together, and what's your situation (dating, married, etc.)?
Just talk naturally, I'll sort the details.
```

---

## Round 1: The Basics

Everything about who they are. One open prompt, let them answer naturally.

**What you need from this round:**
- Names or aliases for both partners
- City and country
- Relationship stage and how long together
- Living situation (cohabiting, separate, long-distance)
- Kids or no kids

**Save immediately to:** `context-library/couple-profile.md`

**As soon as you have their city, silently populate `context-library/local-context.md`:**
- Research and fill in: day trip destinations, nearest airport, short-haul flights,
  climate/seasons, area character. Do this yourself. Do not ask.
- Leave "Local Spots We Already Love" and "Places We've Agreed to Avoid" empty
  for now — those come from the couple in Round 3.

**If they leave gaps:** Fill what you got, ask only the critical missing piece
(location and names are critical — kids and living situation you can infer or
ask later).

**Transition:**

```
Got it. [1-sentence summary of what you captured.]

Round 2: What makes you tick as a couple?

This one matters most — it's what makes suggestions feel personal instead of
generic. Tell me:

What do you actually enjoy doing together? What's on your wishlist to try?
Anything that's been a clear miss? And how would you describe your energy —
are you outdoorsy, homebodies, city explorers, or depends-on-the-week types?

Also useful: food situation (veg, non-veg, allergies), morning vs night people,
introvert vs extrovert.

Throw it all in one message — don't overthink it.
```

---

## Round 2: Personality + Preferences

This is the richest round. Let them talk freely.

**What you need from this round:**
- Shared interests and individual interests
- Activity energy level
- Environment preference (nature / city / mix)
- Personality types (introvert / extrovert)
- Food preferences and restrictions
- Time-of-day preference
- Wishlist items
- Hard nos / things that didn't work

**Save immediately to:** `context-library/preferences.md`

**After saving, give a quick preview to show it's working:**

```
Already getting a picture of you two. [One specific observation that shows
you've been paying attention — something that proves you actually listened,
not a generic compliment.]

Last round — quick one.

Round 3: The practical stuff

What's a comfortable amount to spend on a date? (A range — like "under 2000
rupees no question, 5000 for something special.")

Work schedules, weekend availability, do you have a car or mostly cabs/metro?

And — any local spots you two already love, or places you'd rather I never
suggest?

That's it. Don't overthink the budget part — it's just so I don't suggest
a helicopter ride when you wanted chai by the road.
```

---

## Round 3: Budget + Constraints + Personal Local Knowledge

The logistics round. Keep it light. Only ask what you can't figure out yourself.

**What you need from the couple:**
- Date budget range and splurge ceiling
- Trip budget approach and trips per year
- Budget sensitivity
- Currency (infer from their country if not stated)
- Work schedules
- Weekend availability
- Planning lead time needed
- Transport situation (car / public transport / cabs)
- Local spots they already love (personal knowledge only they have)
- Places to avoid (personal knowledge only they have)
- Health/mobility constraints if any
- Pets if any

**Save immediately to:**
- `context-library/financials.md`
- `context-library/constraints.md`
- Update `context-library/local-context.md` with their personal local spots and avoid list

**If they skip some logistics:** That's fine. Save what you have. Constraints
can always be updated later with `/remember`.

---

## Completion: Show the Payoff

Do NOT end with a dry summary. End with value. Generate their first date idea
right there, using everything you just learned. Follow the `/date-idea` format.

```
All set. Here's what I've got:

[2-3 sentence summary — names, city, vibe, budget range. Keep it tight.]

Your memory files are empty — they'll get richer every time you use
`/remember` after a date or trip.

Now here's the part that matters — your first suggestion, built from
everything you just told me:

---

[Generate a full /date-idea output here — primary + 2 alternatives,
using the date-idea output format. This must reference their specific
context. It must not be generic.]

---

That's what this system does. Run `/date-idea` anytime for a new one,
`/date-batch` for a full month, or `/trip-idea` when you're planning
a getaway.
```

---

## Quality Rules

- Total time must stay under 7 minutes. If it's dragging, you're asking too much.
- Three rounds max. No "one more thing" follow-ups unless critical info is missing.
- Every round transition should feel like a conversation, not a next page.
- The final date idea is mandatory — it's the proof that the onboarding worked.
- Never say "Great answers!" or "Thanks for sharing!" Just move forward.
- NEVER ask the user for information you can derive from their city (geography, climate, airports, nearby destinations). That's your job.
