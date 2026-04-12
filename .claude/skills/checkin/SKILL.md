---
name: checkin
description: Generate five tailored relationship conversation starters. Not therapy — prompts for intentional conversation.
disable-model-invocation: false
user-invocable: true
---

## Quick Start

```
/checkin                    → Five general check-in prompts
/checkin after-date         → Reflection after a recent date
/checkin after-trip         → Reflection after a recent trip
/checkin monthly            → Deeper monthly reflection (10 prompts)
```

**What you get:** Conversation prompts calibrated to their relationship stage,
recent history, and what the system knows about their dynamics.

---

## Scope Boundary (Critical)

This skill produces **conversation prompts** — questions to start intentional
conversations. It does NOT:
- Give relationship advice
- Diagnose or interpret their relationship
- Suggest what they should change or improve
- Act as a therapist or counselor

If the couple seems to want relationship advice, respond:
"I'm not equipped to give relationship advice — that's a conversation for a therapist
or counselor if you need it. What I can do is give you prompts for a good conversation."

---

## Pre-Flight: Context Check

Read:
1. `context-library/couple-profile.md` — Stage, time together
2. `context-library/memory/past-dates.md` — Recent dates (for after-date variant)
3. `context-library/memory/past-trips.md` — Recent trips (for after-trip variant)
4. `context-library/memory/learnings.md` — Known dynamics, patterns

---

## Output Format

```markdown
# Check-In Prompts — [Date]

Five questions worth sitting with. No right answers — just conversation.

---

1. **[Question]**
   *[One sentence of context for why this is worth asking — optional, skip if obvious]*

2. **[Question]**

3. **[Question]**

4. **[Question]**

5. **[Question]**

---
*Find somewhere comfortable, put phones down, and give each other real answers.*
```

---

## Question Quality Rules

Good check-in questions:
- Are open-ended (can't be answered yes/no)
- Are specific enough to not feel generic
- Are calibrated to the couple's stage (a check-in for a couple dating 3 months
  looks very different from one for a couple married 8 years)
- Don't feel clinical or therapeutic
- Are ones you'd want to ask a close friend

Bad check-in questions (avoid these patterns):
- "How are you feeling about our relationship?" (too vague)
- "Do you feel heard?" (leading / therapeutic)
- "What would you rate our communication?" (sounds like a performance review)
- Any question that assumes a problem exists

After-date variants should reference the specific date if it's in memory.
After-trip variants should reference the trip.

---

## Save Output

Save to: `outputs/check-ins/[YYYY-MM-DD]-checkin.md`
