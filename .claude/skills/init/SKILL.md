---
name: init
description: Guided Notion setup — step-by-step walkthrough to create the shared workspace, connect the integration, and verify everything works. Run once per couple.
user-invocable: true
argument-hint: [no arguments needed]
---

## Purpose

Walk the couple through setting up Notion as their shared memory backend.
Interactive, step-by-step — waits for confirmation at each stage.

## What syncs to Notion vs what stays local

| File | Notion page | Syncs? |
|------|-------------|--------|
| couple-profile.md | "Couple Profile" | ✓ |
| preferences.md | "Preferences" | ✓ |
| constraints.md | "Constraints" | ✓ |
| local-context.md | "Local Context" | ✓ |
| **financials.md** | — | **✗ local only — never syncs** |
| memory/past-dates.md | "Past Dates" | ✓ |
| memory/past-trips.md | "Past Trips" | ✓ |
| memory/learnings.md | "Learnings" | ✓ |
| memory/wishlist.md | "Wishlist" | ✓ |
| memory/memory-jar.md | "Memory Jar" | ✓ |
| memory/streak.md | "Streak" | ✓ |
| memory/vibe-check-history.md | "Vibe Check History" | ✓ |
| outputs/surprises/ | — | ✗ local only — never syncs |

## What the user does vs what I do

**User does manually (~10 min):**
- Create a Notion account (free)
- Create ONE top-level page (any name)
- Create the integration token at notion.so/my-integrations
- Connect the integration to that page
- Add the token to their shell profile

**I do automatically once connected:**
- Check for existing pages before creating anything (never duplicate)
- Create all 11 sub-pages with correct structure
- Populate them from local files
- Record all page IDs to sync/notion-setup.md

**Privacy:** Pages must NEVER be made public. Share only with partner
by email (Editor access) via Notion's Share menu. Not shared to web.

## Workflow

### Step 0: Check current state

Check if NOTION_API_KEY environment variable is set.
If yes, test connection via API call.

If already connected and pages exist:
```
Notion is already connected. I can see your pages:
[list pages]
Run /init reset if you want to start fresh, otherwise you're good.
```

If not connected, proceed with Step 1.

### Step 1: Create the Notion page

Say:
```
Let's get Notion set up so both you and [Partner 2 name from couple-profile.md]
can share memories, preferences, and everything the system tracks.

You only need to do 3 things manually — I'll handle the rest once connected.

**Step 1: Create one Notion page**

1. Go to notion.so and sign in (or create a free account — it's free)
2. Create a new top-level page — name it anything you like

Don't create any sub-pages. I'll create all 11 automatically once connected.

Tell me when the page exists and share the page link.
```

Wait for confirmation + page link. Extract the page ID from the URL.
(URL format: notion.so/workspace/Page-Name-[PAGE_ID])

### Step 2: Create the Notion integration

Say:
```
**Step 2: Create the API integration**

1. Go to notion.so/my-integrations
2. Click "+ New integration"
3. Name it: "Couple OS"
4. Select your workspace
5. Click "Submit"
6. Copy the token shown — it starts with ntn_ or secret_

Now connect it to your page:
7. Go back to your Notion page
8. Click the ··· menu (top right)
9. Click "Add connections"
10. Search for "Couple OS" and select it

Paste the token here when ready.
```

Wait for token.

### Step 3: Save the API key

Say:
```
**Step 3: Save to your shell**

Run this in your terminal (separate tab, outside Claude Code):

echo 'export NOTION_API_KEY="[TOKEN]"' >> ~/.zshrc
source ~/.zshrc
launchctl setenv NOTION_API_KEY "[TOKEN]"

The launchctl line makes it available to Claude Code immediately.
The ~/.zshrc line persists it across restarts.

Tell [Partner 2 name] to run the same commands on her machine with the same token.

Restart Claude Code, then run /init again — I'll verify and finish setup.
```

### Step 4: Verify + auto-create all pages

On re-run with NOTION_API_KEY set:

1. Test API connection
2. Search for existing pages to avoid duplicates:
   - If a page with the same name already exists → use it, don't create a new one
   - If it doesn't exist → create it
3. Create missing pages from this list:
   - Couple Profile
   - Preferences
   - Constraints
   - Local Context
   - Past Dates
   - Past Trips
   - Learnings
   - Wishlist
   - Memory Jar
   - Streak
   - Vibe Check History
4. Populate each from local context-library files
5. Record all page IDs to sync/notion-setup.md

Then say:
```
Connected. Here's your Notion workspace:

Profile (both partners see these):
✓ Couple Profile
✓ Preferences
✓ Constraints
✓ Local Context
✗ Financials — stays on your machine only (sensitive data)

Memory (updated after every date, trip, feedback):
✓ Past Dates
✓ Past Trips
✓ Learnings
✓ Wishlist
✓ Memory Jar
✓ Streak
✓ Vibe Check History

**Setup complete.**

One last thing — share the workspace with [Partner 2 name]:
1. Open your Notion page
2. Click "Share" → invite [Partner 2 name]'s email → Editor access
3. Do NOT enable "Share to web" — keep it private between you two

Your shared memory is live. Every /feedback, /remember, and profile
update will now appear for both of you automatically.
```

### Step 5: Record page IDs

Save all page IDs to sync/notion-setup.md (this file is gitignored).

## Tone

- Friendly, practical, patient
- Wait for confirmation between steps — never rush ahead
- If they get stuck, troubleshoot before suggesting they start over
- If pages already exist, use them — never create duplicates
