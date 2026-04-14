# Quality Rules — Applied to Every Suggestion

Before finalizing any output, run these checks silently. Never show this process.

## 1. Not a repeat
Check past-dates.md and past-trips.md. If the suggestion appears there: replace it.

## 2. Budget fits
Check financials.md. Cost must be within stated range. If budget is missing: ask before generating.
Always give specific cost estimates (e.g., "~₹1500") not vague ones ("low cost").

## 3. Not generic
Apply the generic test: Could this suggestion work for any random couple?
If yes: rewrite. The "Why it fits you" section must cite at least 2 real details from their context files.

## 4. Variety check (anti-pattern detection)
Check BOTH sources for clustering:
- `context-library/memory/past-dates.md` — last 3-4 logged dates
- `outputs/suggestion-log.md` — last 5-6 generated suggestions (even if not tried)

If 3+ of the last 5 suggestions share the same category tag (all food, all outdoor,
all cultural, all low-effort): force a different category. The suggestion log catches
patterns that past-dates.md misses (because many suggestions never get logged).

## 5. Seasonally appropriate
Check time of year against their climate in local-context.md. Outdoor beach picnic in peak summer in a 45C city = reject. Flag seasonal conditions honestly.

## 6. Stage-appropriate
A 3-month couple and a 7-year couple get very different suggestions. Check couple-profile.md.

## 7. Memory Jar Protection

/memory-jar entries are never used as input to suggestions.
They are for looking back, not for optimisation.
Never reference a memory jar entry in a /date-idea or /trip-idea output.
The jar is separate from the suggestion engine.

## 8. Milestone Letter Bar

Before writing a /milestone-letter, verify:
- At least 3 entries exist across all memory files combined
- At least one entry contains a specific place, activity, or moment name
If neither is true: ask the couple to add more context before writing the letter.
A letter with no real material is worse than no letter at all.

## 9. Streak Calculation Integrity

Never round up or be generous with streak counts.
A month counts only with a logged date AND a rating. Both required.
Do not count /mood-match suggestions that have no feedback rating.
