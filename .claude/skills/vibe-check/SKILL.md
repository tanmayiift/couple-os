---
name: vibe-check
description: Quarterly 10-question quiz both partners answer separately. Claude compares answers and flags where preferences have diverged since onboarding.
user-invocable: true
argument-hint: [partner1 / partner2 / compare]
---

## Purpose

Relationships change. Preferences shift. Onboarding captured who you were
then — /vibe-check captures who you are now, quarterly.

Run separately by each partner, then run /vibe-check compare to see
where you've grown together or apart.

## Usage

```
/vibe-check partner1    → Quiz for Partner 1
/vibe-check partner2    → Quiz for Partner 2  
/vibe-check compare     → Compare latest answers, flag divergences
/vibe-check             → Defaults to partner1 if no arg given
```

## Pre-Flight: Read Context

Before starting, read couple-profile.md to get partner names, relationship stage,
and how long they've been together. Use their real names throughout, not placeholders.
Also read preferences.md and financials.md — you'll compare answers against these
in compare mode.

## Workflow: Quiz Mode (partner1 or partner2)

Tell the partner which one they are, then ask all 10 questions.
Accept short answers. Don't prompt or guide — capture honest first reactions.

Say this first:
```
Vibe Check — [their actual name from couple-profile.md] — [Month Year]

10 quick questions. Answer honestly, fast. No right answers.
Your partner will answer separately — then we'll compare.
```

### The 10 Questions

1. "On a typical weekend, what does your ideal Saturday look like in one sentence?"

2. "Rate how much you want MORE of each right now (1=less, 5=more):
   Adventure / Quiet time / Social plans / Just the two of you"

3. "One place you haven't been together that you keep thinking about?"

4. "The last date you went on — was it more or less energetic than you wanted?
   (More energetic / About right / Less energetic)"

5. "How often do you want to go on intentional dates? 
   Weekly / Every two weeks / Monthly / Whenever it happens"

6. "Complete this: Right now, our relationship needs more ___"

7. "What's something you've started wanting that you didn't want a year ago?"

8. "Budget for a special occasion — has your comfort zone changed?
   Same as before / A bit more / A bit less / Significantly different"

9. "One thing you wish you did together more that you used to do?"

10. "Pick the one that sounds best right now:
    A) Weekend trip somewhere new
    B) Perfect evening at home
    C) Something active outdoors together
    D) A night out with energy and people"

### After answers collected

Save to Notion Vibe Check History page and local vibe-check-history.md:

```markdown
## [Month Year] — [Partner Name]

Q1: [answer]
Q2: Adventure:[x] Quiet:[x] Social:[x] Just us:[x]
Q3: [answer]
Q4: [answer]
Q5: [answer]
Q6: [answer]
Q7: [answer]
Q8: [answer]
Q9: [answer]
Q10: [answer]

Logged: [DATE]
```

Tell the partner:
```
Saved. Ask your partner to run /vibe-check partner2 when they have 5 minutes.
Then run /vibe-check compare to see where you two stand.
```

## Workflow: Compare Mode (/vibe-check compare)

Read both partners' latest entries from vibe-check-history.md / Notion.

If only one partner has answered: 
```
[Partner 2] hasn't completed their vibe check yet. 
Ask them to run /vibe-check partner2, then come back here.
```

If both have answered, produce a comparison report:

```markdown
## Vibe Check — [Month Year]

### Where you're aligned
[List questions where answers were similar or complementary]

### Where you've drifted
[List questions with meaningfully different answers — be specific, not judgmental]
Example: "[Partner 1] wants more adventure right now. [Partner 2] is leaning toward
quieter evenings. Worth a conversation before the next /date-batch."

### What's changed since onboarding
[Compare Q2, Q5, Q8 answers against preferences.md and financials.md]
[Flag if any answers suggest the profile files need updating]

### Suggested profile updates
[Specific lines in preferences.md or financials.md to update, if answers suggest drift]
Example: "Consider updating preferences.md activity level from 'Moderate' to 'Light'
based on [Partner 2]'s answers."

### One thing to try this month
[Single suggestion that bridges any divergence found]
```

After compare report, ask:
```
Want me to update your preference files based on these answers? 
Say yes and I'll make the specific changes.
```

If yes: update the relevant context files and confirm exactly what changed.
Save updated comparison to Notion Vibe Check History page.
