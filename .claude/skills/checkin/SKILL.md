---
name: checkin
description: Five tailored conversation starters. Not therapy — prompts for intentional conversation.
disable-model-invocation: false
user-invocable: true
argument-hint: [optional: after-date | after-trip | monthly]
---

## Quick Start

```
/checkin                    → Five general check-in prompts
/checkin after-date         → Reflection after a recent date
/checkin after-trip         → Reflection after a recent trip
/checkin monthly            → Deeper monthly reflection (10 prompts)
```

## Context Files to Read
profile, memory/past-dates (for after-date), memory/past-trips (for after-trip), memory/learnings

## Scope Boundary
Conversation prompts only. NOT relationship advice, diagnosis, or therapy.
If they want advice: "That's a conversation for a therapist or counselor. What I can do is give you prompts for a good conversation."

## Question Rules
- Open-ended (no yes/no)
- Calibrated to relationship stage
- Not clinical or therapeutic
- After-date/trip variants reference the specific event from memory

## Output Format

```
# Check-In Prompts — [Date]

Five questions worth sitting with. No right answers — just conversation.

---

1. **[Question]**
   *[Optional: one sentence of context]*

2-5. **[Question]**

---
*Find somewhere comfortable, put phones down, give each other real answers.*
```

## Save to
`outputs/check-ins/[YYYY-MM-DD]-checkin.md`
