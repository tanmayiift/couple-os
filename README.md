# Couple OS

An AI relationship co-pilot built on Claude Code. It learns about you and your
partner — preferences, budget, stage, local context — and generates personalized
suggestions for dates, trips, and shared activities. No generic ideas. No booking.
Just a system that knows you.

## What It Does

| Command | What you get |
|---------|-------------|
| `/onboard` | One-time intake: populates all context files in 20-30 minutes |
| `/date-idea` | One date suggestion for this week + 2 alternatives |
| `/date-batch` | Four dates for the month ahead |
| `/trip-idea` | Destination + what to do there (no hotels/flights) |
| `/activity-pack` | Five shared activities, hobbies, and rituals to try |
| `/checkin` | Five conversation starters tailored to your stage |
| `/remember` | Update context: log what worked, what didn't, what changed |
| `/week-ritual` | One recurring weekly ritual suggestion |

## Setup

**Requirements:** Node.js 18+, Claude.ai account, 20 minutes.

```bash
# Install Claude Code
npm install -g @anthropic-ai/claude-code

# Clone and launch
git clone https://github.com/tanmayiift/couple-os.git
cd couple-os
claude

# Run onboarding
/onboard
```

See `setup/installation-guide.md` for full instructions.

## How It Works

Couple OS is a Claude Code project — a structured directory that Claude Code reads
automatically. All intelligence lives in two places:

1. **Context files** (`context-library/`) — Who you are, what you like, what you've
   done. You fill these in during `/onboard` and update them with `/remember`.

2. **Skills** (`.claude/skills/`) — The slash commands. Each one knows which context
   files to read, what quality standards to enforce, and how to save output.

There's no app, no server, no account, and no subscription. Everything runs locally.

## Privacy

All your data stays on your machine. The context files you fill in during onboarding
are plain markdown files stored in this directory. Nothing is sent to any server
except your prompts to Claude via the Claude Code API (same as any Claude conversation).

You can use aliases instead of real names. You can skip any questions you're not
comfortable answering — though more detail means better suggestions.

## Customization

This is a template. Everything is meant to be changed:
- Edit `context-library/` files directly anytime
- Add your own commands to `.claude/skills/`
- Extend the sub-agents in `sub-agents/`
- Change the output formats in the SKILL.md files

## Contributing

PRs welcome. Especially interested in:
- New slash commands (anniversary planner, season bucket list, etc.)
- Improved context templates
- Better output format variations
- Non-English versions

## License

MIT — use it, fork it, ship it.
