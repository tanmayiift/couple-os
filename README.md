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
- Run `/feedback` after any date or trip for a quick 4-question debrief (includes sentiment tags)
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
│   ├── surprise/SKILL.md             # Surprise planner (local only)
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
│   ├── letters/                      # Milestone letters
│   └── surprises/                    # Surprise plans (gitignored)
└── setup/
    ├── installation-guide.md
    └── first-session-checklist.md
```

---

## Privacy

All personal data stays on your machine by default. The context files (your names, budget, preferences) are plain markdown in this directory and are gitignored.

**Optional Notion sync:** Run `/init` to set up a shared Notion workspace with your partner. When connected, memory files (past dates, learnings, wishlist, memory jar, etc.) sync to Notion so both partners see the same data. Local markdown files stay as backup. The 5 core profile files (couple-profile, preferences, financials, constraints, local-context) never sync — they stay local only.

**What you do vs what Claude does during `/init`:**
- You create: one Notion account, one top-level page ("Couple OS Memory"), one integration token. That's it.
- Claude creates: all 7 sub-pages automatically once connected. No manual page creation needed.

**Notion pages are private, not public.** Share only with your partner via email (Editor access) through Notion's Share menu. Never enable "Share to web."

`/surprise` outputs never sync to Notion. Ever. The whole point is that the other partner doesn't see it coming.

Nothing else is sent to any server except your prompts to Claude via the standard Claude Code API (same as any Claude conversation).

You can use aliases instead of real names. You can skip any question during onboarding. More detail means better suggestions, but it's always your call.

---

## Customization

This is a template. Everything is meant to be changed:
- Edit `context-library/` files directly anytime
- Add your own slash commands to `.claude/skills/`
- Modify output formats in any SKILL.md
- Adjust quality rules in `sub-agents/quality-rules.md`

---

## Personalisation Engine

Couple OS doesn't just track what you've done — it learns *why* things worked.

**Sentiment tags.** After each date, `/feedback` asks what made it work. Tags like `intimate`, `new-discovery`, `energising`, `creative`, `social` get stored against your dates. After 5+ entries, the system identifies your dominant positive tags and biases new suggestions toward them.

**Seasonal patterns.** Every logged date is auto-tagged with season + indoor/outdoor. After 6+ months, the system knows your seasonal patterns ("more home dates in monsoon, more outdoor dates in autumn") and calibrates accordingly.

**Anti-pattern detection.** Every suggestion the system generates — even ones you don't try — is logged to `outputs/suggestion-log.md`. Before generating a new one, it checks the log to avoid clustering. If 3 of the last 5 were food-based, it forces a different category.

**Anniversary proximity.** Reads your anniversary date from your profile. Within 30 days of it, biases one suggestion toward "milestone-worthy." Within 7 days, makes the primary suggestion anniversary-calibrated.

**Relationship phase awareness.** Year 1 couples get "still discovering each other" energy. Year 5+ get "surprise me" energy. The system reads your stage and adjusts.

**Partner-specific weighting.** `/date-idea for-[name]` generates something that leans 70% toward one partner's preferences while keeping the other partner engaged in a supporting role.

---

## Command Details

### `/onboard` — First-Time Setup

Five conversational blocks: profile, preferences, financials, constraints, local context. Geography (nearby cities, airports, climate) is auto-populated from your city — you only answer things only you would know. Ends with your first `/date-idea` on the spot.

### `/init` — Notion Setup (Optional)

Interactive guided setup for shared memory between partners. Run once per couple, skip if you only want local storage.

**What you do manually (~10 min):**
1. Create a free Notion account at notion.so
2. Create one top-level page called "Couple OS Memory"
3. Go to notion.so/my-integrations → create an integration called "Couple OS" → copy the `secret_` token
4. Connect the integration to your page (··· menu → Add connections)
5. Add `export NOTION_API_KEY="your_token"` to `~/.zshrc` and restart Claude Code
6. Share the page with your partner by email (Editor access) — keep it private, never enable "Share to web"

**What Claude does automatically:**
- Creates all 7 sub-pages (Past Dates, Past Trips, Learnings, Wishlist, Memory Jar, Streak, Vibe Check History)
- Populates structure, records page IDs, verifies the connection

Run `/init` and it walks through every step interactively.

### `/date-idea` — Weekly Date Suggestion

Flags: `low-effort`, `splurge`, `outdoor`, any weekday name, or `for-[partner-name]`.

Returns 1 primary suggestion + 2 alternatives at different effort levels. Reads sentiment patterns, seasonal patterns, and anniversary proximity. The `for-[name]` variant leans into one partner's individual preferences.

### `/mood-match` — Energy-Calibrated Tonight

The daily layer missing from `/date-idea`. Asks two questions first — energy level (1-5) and mood (adventurous / cosy / social / just us) — then suggests one thing calibrated to right now. No alternatives, no padding. For decisive evenings.

### `/date-batch` — Monthly Date Plan

Four dates for the month. Engineered for variety: at least 1 indoor + 1 outdoor, at least 1 free + 1 paid, at least 1 weeknight-friendly, no two in the same category.

### `/trip-idea` — Trip Destination

Flags: `weekend`, `week`, `long-haul`, any season, or `options` (for 3 brief picks). Deep-dive format: what to do, day structure, food culture, activity budget, best time, why it fits. No hotel or flight recommendations. Reads anniversary proximity and sentiment patterns.

### `/activity-pack` — Shared Activities

Five non-date activities: new hobbies, recurring rituals, creative projects, physical anchors. Mix of one-time and recurring. Each includes a specific first step so you can start this week.

### `/checkin` — Conversation Starters

Five open-ended questions calibrated to your relationship stage. Not therapy. Variants: `after-date`, `after-trip`, `monthly` (10 prompts).

### `/week-ritual` — Weekly Ritual

One small recurring habit: anchored to a specific time, sustainable, specific to your life. Appended to a running list so you build a collection.

### `/vibe-check` — Quarterly Preference Quiz

Both partners answer the same 10 questions separately, then `/vibe-check compare` produces a divergence report. Catches preference drift since onboarding and suggests profile updates. Run quarterly.

### `/memory-jar` — Favourite Moments Log

Add or read favourite shared moments. Not dates — the small things worth keeping. The wrong turn that became a story. The Sunday on the terrace. Run `/memory-jar read` on bad days. Memory jar entries are *never* used as input to suggestions — they exist only for looking back.

### `/milestone-letter` — Letters in Your Voice

Reads everything — past dates, trips, learnings, memory jar, wishlist — and writes a short letter to you about the period just passed. Variants: `anniversary`, `after-trip`, `monthly`, or any custom milestone. Letters get longer and more specific the more you use the system.

### `/streak` — Date Habit Tracker

Shows consecutive months of logged dates with feedback. Quiet milestone messages at 1, 3, 6, 12, 18, 24 months. Broken streaks reset without shame. The habit is the reward.

### `/surprise [partner-name]` — Surprise Planner (Local Only)

One partner runs it solo. Reads the recipient's individual preferences (personality, interests, comfort zones) and generates a plan calibrated specifically for them, with the planner in the supporting role. Includes a setup checklist, timing, and a backup plan. **Never syncs to Notion.** Stays in `outputs/surprises/` (gitignored) until the couple chooses to log it via `/feedback` after the fact.

### `/feedback` — Post-Activity Debrief

Four questions: What was it? How did it go? What made it work (sentiment tags)? One thing to remember? Auto-tags the entry with season, setting (indoor/outdoor), and category. Updates past-dates, learnings (sentiment + seasonal patterns), and the suggestion log. Under 2 minutes. This is what makes future suggestions smarter.

### `/remember` — Update Anything

Natural language updates to any context or memory file. "We loved the hiking date." "Partner gets anxious in crowds." "We're moving to Berlin in October." Routes to the right file and syncs to Notion if connected.

---

## Contributing

PRs welcome. Especially interested in:
- New slash commands (anniversary planner, seasonal bucket list, etc.)
- Better output formats
- Non-English locale support
- Quality-of-life improvements

---

## Changelog

### v1.2 — Notion sync, emotional memory, personalisation engine
- 7 new skills: `/mood-match`, `/vibe-check`, `/memory-jar`, `/milestone-letter`, `/streak`, `/surprise`, `/init`
- Optional shared memory via Notion MCP — both partners see the same data
- Sentiment tags on every feedback (13 tags) — system learns *why* dates work
- Seasonal pattern tracking — auto-calibrates to your time of year after 6+ months
- Partner-specific date suggestions via `/date-idea for-[name]`
- Anti-pattern detection via suggestion log — catches clustering before it happens
- Anniversary proximity detection in date-idea and trip-idea
- Relationship phase awareness (Year 1 vs 5+ get different energy)
- Quality rules expanded from 6 to 9

### v1.1 — Auto-learning and feedback
- Added `/feedback` skill with 3-question debrief
- Auto-learning protocol — captures preferences from natural conversation
- Token optimization across all skills
- README improvements

### v1.0 — Initial release
- 9 core skills: `/onboard`, `/date-idea`, `/date-batch`, `/trip-idea`, `/activity-pack`, `/checkin`, `/week-ritual`, `/remember`, `/feedback`
- Local-first context library
- Quality rules engine

---

## License

MIT — use it, fork it, make it yours.
