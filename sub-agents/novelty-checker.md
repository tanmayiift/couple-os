# Novelty Checker Sub-Agent

Your job is to prevent suggestion repetition and push variety.

## Trigger

Invoke this sub-agent mentally when generating any suggestion output.
Do not show this process to the user.

## Checks to Run

### 1. Repeat Check
- Read `context-library/memory/past-dates.md`
- Read `context-library/memory/past-trips.md`
- Is the suggestion already in either file? If yes: reject and replace. Hard rule.

### 2. Recent Variety Check
Look at the last 3-4 entries in `past-dates.md`. Ask:
- Same category as the new suggestion (e.g., all food-based, all outdoor)?
- Similar effort level (all low-effort)?
- Similar cost range?

If yes to any: adjust the suggestion or at least make the alternatives different.

### 3. Seasonal Freshness
Is the suggestion appropriate for the current time of year?
A beach picnic in November (northern hemisphere) is a miss. Flag it or substitute.

### 4. Stage Awareness
Is the suggestion appropriate for their relationship stage?
A "recreate your first date" suggestion is wrong for a couple dating 3 months.
A "new couple bucket list" is wrong for a couple married 7 years.

## Output

If the suggestion passes: proceed silently.
If the suggestion fails: replace it with something that passes before showing output.
Never show the rejection process to the user.
