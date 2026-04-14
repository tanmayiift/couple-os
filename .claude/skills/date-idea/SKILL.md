---
name: date-idea
description: Generate a personalized date suggestion for this week or weekend. Always 1 primary + 2 alternatives.
disable-model-invocation: false
user-invocable: true
argument-hint: [optional: low-effort | splurge | outdoor | weekday name]
---

## Quick Start

```
/date-idea                  → Best fit for this week (couple-consensus)
/date-idea low-effort       → Minimal planning, low cost
/date-idea splurge          → Special occasion, higher budget OK
/date-idea outdoor          → Must involve outdoors/nature
/date-idea tuesday          → Optimized for a weeknight
/date-idea for-[name]       → Leans into one partner's preferences (other supports)
```

## Context Files to Read
profile, preferences, financials, constraints, local-context, memory/past-dates, memory/learnings, memory/wishlist

## Anniversary & Milestone Detection

Before generating, check couple-profile.md for the wedding/anniversary date.

**Within 30 days of anniversary:**
- Bias 1 of the 3 suggestions toward "milestone-worthy" — something they haven't
  done before, slightly above normal effort, worth remembering.
- Add a line: "Your anniversary is [N] days away — this could double as a celebration."

**Within 7 days of anniversary:**
- Make the PRIMARY suggestion anniversary-calibrated. Pull from wishlist items
  they haven't tried yet. Frame it as a first-anniversary / Nth-anniversary plan.
- Flag it explicitly: "Your [Nth] anniversary is [date]. This one's built for it."

**Relationship phase awareness:**
- Year 1: "still discovering each other" energy. Suggest firsts — first dance class,
  first trip to a new city, first time trying something from their wishlist.
- Year 2-3: "deepening" energy. More intentional, more personal, less about novelty.
- Year 5+: "surprise me" energy. Push further outside the pattern.
- Year 10+: "legacy" energy. Experiences that become traditions.

## Workflow
1. Check flag from arguments. Check season, day of week.
2. **If `for-[name]` flag:** Read preferences.md and identify the named partner's
   individual preferences (personality, interests, energy patterns). Generate candidates
   that lean 70% toward the named partner's tastes while keeping the other partner
   engaged. The "Why it fits you" section should explain why the named partner will
   especially love this AND how the other partner fits in.
   Read couple-profile.md and preferences.md to identify each partner's individual
   interests, personality, and comfort zones. Generate candidates that lean 70% toward
   the named partner's specific tastes from their profile while keeping the other
   partner engaged in a supporting role that matches their own comfort level.
3. **If sentiment data exists in learnings.md:** Check the Sentiment Patterns table.
   Bias toward dominant positive tags (e.g., if `intimate` + `new-discovery` score highest,
   lean toward dates with those qualities). Avoid tags marked under "Tags to avoid."
4. **If seasonal data exists in learnings.md:** Check Seasonal Patterns table for the
   current season. Prefer indoor/outdoor based on what's historically rated highest
   this time of year. If no data yet, use climate from local-context.md as default.
5. Generate 6-8 candidates silently. Discard repeats, budget violations, bad fits.
6. **Check suggestion-log.md** for recent suggestions (even unlogged ones). Avoid
   clustering — if last 3 suggestions were food-based, push away from food.
7. Select 3: 1 primary + 2 alternatives at different effort levels.
8. Apply quality rules from `sub-agents/quality-rules.md`.

## Output Format

```
# Date Idea — [YYYY-MM-DD]

## This Week: [Title]

**What:** [2-3 sentences. Specific, visual, actionable.]
**Why it fits you:** [1-2 sentences citing their actual context.]
**Time needed:** [X hours]
**Approximate cost:** [specific range in their currency]
**Best day:** [recommendation]
**One thing to sort in advance:** [only if needed — skip if spontaneous]

---

## If That Doesn't Land

**Lower effort:** [Title] — [2 sentences. Cost and time.]
**Higher energy:** [Title] — [2 sentences. Cost and time.]

---
*Done this? Tell me how it went — or run /feedback for a quick debrief.*
```

## Save to
`outputs/dates/[YYYY-MM-DD]-date-idea.md`

Also append the PRIMARY suggestion to `outputs/suggestion-log.md`:
`| [YYYY-MM-DD] | /date-idea | [Title] | [category tag] | [indoor/outdoor] | suggested |`

Category tags: `food` | `adventure` | `cultural` | `active` | `relaxation` | `home` | `class` | `social`
