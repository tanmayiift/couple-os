# Couple OS

An AI relationship co-pilot built on [Claude Code](https://claude.ai/code). It learns about you and your partner and generates experiences that feel like they came from someone who's known you for years. Not a generic recommendation engine. Not a therapist. Just a system that gets you.

Everything runs locally. No app, no server, no subscription.

---

## What It Does

### Daily
| Command | What it does |
|---------|-------------|
| `/mood-match` | Date idea calibrated to tonight's energy — asks 2 questions first |
| `/date-idea` | Best date for this week + 2 alternatives |
| `/date-idea for-[name]` | Date that leans into one partner's preferences |
| `/surprise [name]` | Plan a surprise for your partner (stays local, never syncs) |

### Planning
| Command | What it does |
|---------|-------------|
| `/date-batch` | 4 dates for the month ahead |
| `/trip-idea` | Next getaway — destination + what to do (no hotels/flights) |
| `/activity-pack` | 5 shared activities, hobbies, rituals to try |
| `/week-ritual` | One recurring weekly ritual to add |

### Know Each Other Better
| Command | What it does |
|---------|-------------|
| `/vibe-check` | Quarterly quiz — both answer separately, then compare |
| `/checkin` | Conversation starters tailored to your stage |

### Capture and Celebrate
| Command | What it does |
|---------|-------------|
| `/memory-jar` | Add or read favourite shared moments |
| `/milestone-letter` | A letter in your own voice about the period just passed |
| `/streak` | Consecutive months of logged dates — your habit score |

### System
| Command | What it does |
|---------|-------------|
| `/onboard` | One-time intake — populates all context files |
| `/init` | Guided Notion setup — connects shared memory with your partner |
| `/feedback` | Rate the date — updates memory, improves suggestions |
| `/remember` | Tell the system anything new about you |

Every suggestion includes a title, time estimate, cost estimate, and a "why it fits you" section that references your actual context. If a suggestion could apply to any random couple, the system rewrites it.

---

## Quick Start

### Prerequisites
- [Node.js 18+](https://nodejs.org)
- A [Claude.ai](https://claude.ai) account (any plan)

### Install

```bash
# Install Claude Code
npm install -g @anthropic-ai/claude-code

# Clone and enter the project
git clone https://github.com/tanmayiift/couple-os.git
cd couple-os

# Launch
claude
```

### First Run

```
/onboard
```

That's it. Three quick rounds of conversation (who you are, what you like, practical stuff), and then the system generates your first personalized date idea right there. Takes about 5 minutes.

After that, run `/date-idea` anytime you need a plan.

---

## How It Gets Smarter Over Time

Couple OS starts useful and gets better the more you use it.

**Active feedback:**
- Run `/feedback` after any date or trip for a quick 3-question debrief
- Run `/remember` anytime to tell it something new ("partner hates loud restaurants," "we want to try kayaking")

**Passive learning:**
- During any conversation, if you mention a preference or reaction, it'll ask: "Want me to note that?"
- After every suggestion it saves, it appends a prompt: "Done this? Tell me how it went."

**What it tracks (local + Notion sync):**
- `memory/past-dates.md` — dates tried + ratings (avoids repeats)
- `memory/past-trips.md` — trips taken (avoids repeat destinations)
- `memory/learnings.md` — discovered preferences ("prefers small venues," "best dates are unplanned")
- `memory/wishlist.md` — things you've said you want to try
- `memory/memory-jar.md` — favourite shared moments, in your own words
- `memory/streak.md` — consecutive months of logged dates
- `memory/vibe-check-history.md` — quarterly preference snapshots from both partners

When Notion is connected (via `/init`), all memory syncs to a shared Notion workspace so both partners see the same data. Local files stay as backup.

The richer these files get, the more specific every suggestion becomes.

---

## Project Structure

```
couple-os/
├── CLAUDE.md                          # System brain — read every session
├── .claude/skills/                    # Slash commands
│   ├── onboard/SKILL.md              # First-time setup
│   ├── init/SKILL.md                 # Notion integration setup
│   ├── date-idea/SKILL.md            # Weekly date suggestion
│   ├── date-batch/SKILL.md           # Monthly date plan
│   ├── mood-match/SKILL.md           # Energy-calibrated date tonight
│   ├── trip-idea/SKILL.md            # Trip destination + concept
│   ├── activity-pack/SKILL.md        # Shared hobbies and rituals
│   ├── checkin/SKILL.md              # Conversation starters
│   ├── vibe-check/SKILL.md           # Quarterly preference quiz
│   ├── memory-jar/SKILL.md           # Favourite moments log
│   ├── milestone-letter/SKILL.md     # Anniversary/milestone letters
│   ├── streak/SKILL.md               # Date habit tracker
│   ├── week-ritual/SKILL.md          # Weekly ritual builder
│   ├── remember/SKILL.md             # Update any context
│   └── feedback/SKILL.md             # Post-date debrief
├── context-library/                   # Your couple profile (gitignored)
│   ├── couple-profile.md
│   ├── preferences.md
│   ├── financials.md
│   ├── constraints.md
│   ├── local-context.md
│   └── memory/
│       ├── past-dates.md
│       ├── past-trips.md
│       ├── learnings.md
│       ├── wishlist.md
│       ├── memory-jar.md             # Favourite shared moments
│       ├── streak.md                 # Date habit tracking
│       └── vibe-check-history.md     # Quarterly preference snapshots
├── context-library/*.template.md      # Blank templates (shipped with repo)
├── sync/notion-setup.md               # Notion integration guide
├── sub-agents/quality-rules.md        # Output quality enforcement
├── outputs/                           # Generated suggestions
│   ├── dates/
│   ├── trips/
│   ├── activities/
│   ├── check-ins/
│   └── letters/                      # Milestone letters
└── setup/
    ├── installation-guide.md
    └── first-session-checklist.md
```

---

## Privacy

All data stays on your machine. The context files (your names, budget, preferences) are plain markdown in this directory. They're gitignored by default so they never get committed.

Nothing is sent to any server except your prompts to Claude via the standard Claude Code API (same as any Claude conversation).

You can use aliases instead of real names. You can skip any question during onboarding. More detail means better suggestions, but it's always your call.

---

## Customization

This is a template. Everything is meant to be changed:
- Edit `context-library/` files directly anytime
- Add your own slash commands to `.claude/skills/`
- Modify output formats in any SKILL.md
- Adjust quality rules in `sub-agents/quality-rules.md`

---

## Command Details

### `/onboard` — First-Time Setup

Three conversational rounds:
1. **Who are you two?** Names, city, relationship stage, living situation
2. **What makes you tick?** Interests, food, energy level, wishlist, hard nos
3. **Logistics and money** Budget, schedules, transport, local favorites

Geography (nearby cities, airports, climate) is auto-populated from your city. You only answer things only you would know.

Ends by generating your first `/date-idea` so you see the payoff immediately.

### `/date-idea` — Weekly Date Suggestion

Flags: `low-effort`, `splurge`, `outdoor`, or any weekday name.

Returns 1 primary suggestion with full detail + 2 alternatives at different effort levels. References your preferences, budget, and location. Checks past dates to avoid repeats.

### `/date-batch` — Monthly Date Plan

Four dates for the month. Engineered for variety:
- At least 1 indoor + 1 outdoor
- At least 1 free + 1 paid
- At least 1 weeknight-friendly
- No two in the same category

### `/trip-idea` — Trip Destination

Flags: `weekend`, `week`, `long-haul`, any season, or `options` (for 3 brief picks).

Deep-dive format: what to do there, day structure, food culture, activity budget, best time to visit, and why it fits you specifically. No hotel or flight recommendations.

### `/activity-pack` — Shared Activities

Five non-date activities: new hobbies, recurring rituals, creative projects, physical anchors. Mix of one-time and recurring. Each includes a specific first step so you can start this week.

### `/checkin` — Conversation Starters

Five open-ended questions calibrated to your relationship stage. Not therapy. Variants: `after-date`, `after-trip`, `monthly` (10 prompts).

### `/week-ritual` — Weekly Ritual

One small recurring habit: anchored to a specific time, sustainable, and specific to your life. Appended to a running list so you build a collection over time.

### `/feedback` — Post-Activity Debrief

Three questions: What was it? How did it go? One thing to remember?
Updates memory files automatically. Under 2 minutes. This is what makes future suggestions smarter.

### `/remember` — Update Anything

Natural language updates to any context file. "We loved the hiking date." "Partner gets anxious in crowds." "We're moving to Berlin in October." It routes to the right file and confirms what changed.

---

## Contributing

PRs welcome. Especially interested in:
- New slash commands (anniversary planner, seasonal bucket list, etc.)
- Better output formats
- Non-English locale support
- Quality-of-life improvements

---

## License

MIT — use it, fork it, make it yours.
