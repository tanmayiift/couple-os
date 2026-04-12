# Installation Guide

## Prerequisites

- Node.js 18 or newer — [nodejs.org](https://nodejs.org)
- A Claude.ai account (free tier works)
- Git (to clone the repo)

## Step 1: Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
claude --version
```

## Step 2: Clone the Repo

```bash
git clone https://github.com/tanmayiift/couple-os.git
cd couple-os
```

## Step 3: Launch Claude Code

```bash
claude
```

Claude Code will read `CLAUDE.md` automatically on startup.

## Step 4: Run Onboarding

In your Claude Code session:

```
/onboard
```

This is the only setup required. It takes 20-30 minutes and populates all
your context files. Once done, every other command works.

## Verifying Setup

After onboarding, run:
```
/date-idea
```

You should get a suggestion that references your city, budget range, and preferences.
If it feels generic, some context files may not have been fully populated.
Run `/onboard update` to fill any gaps.
