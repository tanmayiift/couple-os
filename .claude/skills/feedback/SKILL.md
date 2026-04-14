---
name: feedback
description: Quick debrief after a date, trip, or activity. Four questions, under 2 minutes, auto-updates memory with sentiment tags and seasonal data.
disable-model-invocation: false
user-invocable: true
argument-hint: [optional: what you did]
---

## Quick Start

```
/feedback                          → Start a debrief
/feedback hiking date last weekend → Skip Q1, jump to rating
```

**What you get:** Memory files updated with rating, learning, sentiment tags,
and season data. Future suggestions reflect what worked, why it worked, and
what time of year works best.

**Time:** Under 2 minutes.

---

## Workflow

If an argument was provided (e.g., "hiking date last weekend"), use it as the answer
to Q1 and skip straight to Q2.

Otherwise, ask exactly these four questions in order. Accept short answers.

**Q1:** "What was it? (the date, trip, or activity — name or describe it briefly)"

**Q2:** "How did it go?"
Accept natural language. Map to rating internally:
- Loved it / amazing / best ever → ❤️
- Good / solid / enjoyed it → 👍
- Meh / mixed / okay → 👍 with a note
- Bad / miss / didn't work → 👎

**Q3:** "What made it work (or not)? Pick any that apply, or say it in your own words:"
```
Tags: new-discovery | intimate | energising | relaxing | creative | social |
      adventurous | familiar-comfort | food-highlight | too-crowded | too-expensive |
      wrong-energy | bad-timing
```
Accept their own words too — map to the closest tag(s) internally.
Multiple tags are fine and encouraged.

**Q4:** "One thing worth remembering for next time?"
This is the learning. Accept anything: "venue was too loud," "the sunset timing
was perfect," "skip the appetizers," "do this again in winter."

---

## Auto-Tagging (Done Silently)

After collecting answers, Claude determines these tags automatically — do NOT ask:

**Season tag:** Based on the date of the activity:
- Apr-Jun → `summer`
- Jul-Sep → `monsoon`
- Oct-Nov → `autumn`
- Dec-Feb → `winter`
- Feb-Mar → `spring`

**Setting tag:** Based on the activity description:
- `indoor` or `outdoor` or `mixed`

**Category tag:** Based on the activity type:
- `food` | `adventure` | `cultural` | `active` | `relaxation` | `home` | `travel` | `class` | `social`

---

## After Collecting Answers

Update the right files:

1. **If it was a date or activity:** Add entry to `context-library/memory/past-dates.md`
   Format: `| [YYYY-MM-DD] | [Title] | [❤️/👍/👎] | [sentiment tags] | [season:setting] | [Note from Q4] |`

2. **If it was a trip:** Add entry to `context-library/memory/past-trips.md`
   Format: `| [YYYY-MM] | [Destination] | [Duration] | [❤️/👍/👎] | [sentiment tags] | [Note] |`

3. **If Q4 contains a preference signal:** Also add to `context-library/memory/learnings.md`
   under `## General Preferences`:
   Format: `- [YYYY-MM-DD]: [Observation]`

4. **Update Sentiment Patterns in learnings.md:**
   Under `## Sentiment Patterns`, update the tag count table:
   - Increment count for each sentiment tag used
   - Update "Last seen" date
   - After 5+ entries: calculate "Dominant positive tags" and "Tags to avoid"
     (tags that appear on ❤️-rated dates vs 👎-rated dates)

5. **Update Seasonal Patterns in learnings.md:**
   Under `## Seasonal Patterns`, update the season row:
   - Increment indoor/outdoor count for the relevant season
   - Update average rating for that season
   - After 6+ months of data: add pattern notes
     (e.g., "Best outdoor dates: Oct-Nov. Avoid outdoor plans Jun-Aug.")

6. **Update suggestion-log.md:**
   If the date came from a system suggestion (check outputs/suggestion-log.md),
   mark it as "done + [rating]" in the log.

7. **Write to Notion + local** (except /surprise dates — those are local only until
   the couple explicitly logs them via /feedback)

---

## Confirmation

```
Got it. Updated [files changed]:
→ [what was logged, one line]
→ Tagged: [sentiment tags] | [season:setting]

[If a learning was extracted:] Also noted: "[learning]"
[If a sentiment pattern emerged:] Pattern update: your best dates tend to be [dominant tags].
```

No follow-up questions. Keep it fast. Done.
