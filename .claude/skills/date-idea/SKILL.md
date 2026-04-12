---
name: date-idea
description: Generate a personalized date suggestion for this week or weekend. Always 1 primary + 2 alternatives.
disable-model-invocation: false
user-invocable: true
---

## Quick Start

```
/date-idea                  → Best fit for this week (default)
/date-idea low-effort       → Minimal planning, low energy, low cost
/date-idea splurge          → Special occasion feel, higher budget OK
/date-idea outdoor          → Must involve outdoors/nature
/date-idea tuesday          → Optimized for a weeknight
```

**What you get:** 1 primary date suggestion with full detail, plus 2 alternatives
at different effort levels. Saved to `outputs/dates/`.

**Time:** 2-3 minutes.

---

## Pre-Flight: Context Check

Read these files before generating anything:

1. `context-library/couple-profile.md` — Names, stage, living situation
2. `context-library/preferences.md` — Activity level, interests, dislikes
3. `context-library/financials.md` — Date budget range
4. `context-library/constraints.md` — Weekend availability, transport
5. `context-library/local-context.md` — City, nearby options
6. `context-library/memory/past-dates.md` — What's been done (avoid repeats)
7. `context-library/memory/learnings.md` — Discovered preferences

**If context files are empty:** Do not generate. Respond:
```
Context files are empty. Run /onboard first — it takes 20 minutes and makes
every suggestion after this specific to you.
```

**If only some files are sparse:** Ask the missing questions before proceeding.
Never generate with unknown budget or location.

---

## Workflow

### Step 1: Situation Assessment

Identify:
- Day of week and approximate time of year (affects energy, light, weather)
- Any flag from the command (`low-effort`, `splurge`, `outdoor`, day-specific)
- What's been suggested recently in `memory/past-dates.md`
- Any wishlist items in `memory/wishlist.md` that fit the current context

### Step 2: Idea Generation (Internal)

Generate 6-8 candidate ideas silently. Do not show these to the user.

For each candidate, check:
- Is it in `memory/past-dates.md`? If yes, discard.
- Does it fit the budget? If no, discard unless `splurge` flag.
- Does it match the energy level of the flag? If no, adjust.
- Does it require conditions (weather, advance booking) that should be flagged?
- Does it reference something specific from their context?

Select 3 survivors: 1 primary (best overall fit) and 2 alternatives (different
effort levels from the primary).

### Step 3: Write Output

Use the output format below. Be specific. One sentence of personalization minimum
per suggestion. Reference their names, their preferences, their constraints.

---

## Output Format

```markdown
# Date Idea — [Date: YYYY-MM-DD]

## This Week: [Suggestion Title]

**What:** [2-3 sentence description. Specific, visual, actionable.]

**Why it fits you:** [1-2 sentences connecting to their actual context — preferences,
stage, recent history, something from learnings.md.]

**Time needed:** [X hours]
**Approximate cost:** [$ range, specific]
**Best day:** [Day recommendation]
**One thing to sort in advance:** [Only include if relevant — booking, ingredients,
weather check, etc. Skip this line if truly spontaneous.]

---

## If That Doesn't Land

**Lower effort:** [Title] — [2-sentence description. Cost and time.]

**Higher energy:** [Title] — [2-sentence description. Cost and time.]

---
*Use `/remember we tried [suggestion title], it was [good/great/a miss]` after so
future suggestions keep improving.*
```

---

## Quality Checks (Run Before Saving)

- [ ] Primary suggestion cannot apply to a random couple — it references their specific context
- [ ] Not in `memory/past-dates.md`
- [ ] Budget is within stated range (or flagged if splurge)
- [ ] Time estimate is realistic
- [ ] "Why it fits you" section cites something real from context files
- [ ] At least one alternative is lower effort than the primary
- [ ] No generic filler phrases

---

## Save Output

Save to: `outputs/dates/[YYYY-MM-DD]-date-idea.md`
