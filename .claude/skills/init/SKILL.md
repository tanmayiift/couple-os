---
name: init
description: Guided Notion setup — step-by-step walkthrough to create the shared workspace, connect the integration, and verify everything works. Run once per couple.
user-invocable: true
argument-hint: [no arguments needed]
---

## Purpose

Walk the couple through setting up Notion as their shared memory backend.
This replaces the manual instructions in sync/notion-setup.md with an
interactive, step-by-step guide that waits for confirmation at each stage.

## What the user has to do vs what I do

**User does (manual, requires a browser):**
- Create a Notion account (if they don't have one)
- Create one top-level page called "Couple OS Memory"
- Create the Notion integration and copy the token
- Connect the integration to that page
- Add the token to their shell profile

**I do automatically (once connected):**
- Create all 7 sub-pages inside "Couple OS Memory"
- Populate them with the correct structure
- Record the page IDs
- Verify the connection

**Privacy:** Pages should NEVER be made public. Share only with the partner
by email (Editor access) via Notion's Share menu. Not shared to web.

## Workflow

### Step 0: Check current state

Check if NOTION_API_KEY environment variable is already set.
If yes, attempt a Notion read to verify connection.

If already connected:
```
Notion is already connected. I can see your pages.
Run /init reset if you want to start fresh, otherwise you're good.
```

If not connected, proceed with Step 1.

### Step 1: Create the Notion workspace

Say:
```
Let's get Notion set up so both you and [Partner 2 name from couple-profile.md] can share memories,
dates, and everything else from this system.

You only need to do 3 things manually — I'll handle the rest once connected.

**Step 1: Create one Notion page**

1. Go to notion.so and sign in (or create a free account — it's free)
2. Create a new top-level page called "Couple OS Memory"

That's it for now. Don't create any sub-pages — I'll create all 7 automatically
once the connection is live.

Tell me when the page exists.
```

Wait for confirmation before proceeding.

### Step 2: Create the Notion integration

Say:
```
**Step 2: Create the API integration**

This is what lets me read and write to your Notion pages.

1. Go to notion.so/my-integrations
2. Click "+ New integration"
3. Name it: "Couple OS"
4. Select your workspace
5. Click "Submit"
6. You'll see an "Internal Integration Secret" — copy it (starts with `secret_`)

Now connect it to your page:
7. Go back to your "Couple OS Memory" page in Notion
8. Click the ··· menu (top right)
9. Click "Add connections"
10. Search for "Couple OS" and select it

Paste the secret token here when ready. I won't store it in any file —
it goes straight to your shell profile.
```

Wait for the token.

### Step 3: Save the API key

When they paste the token, verify it starts with `secret_`.

Say:
```
**Step 3: Save to your shell**

Run this in your terminal (a separate tab, outside Claude Code):

echo 'export NOTION_API_KEY="[THEIR_TOKEN]"' >> ~/.zshrc
source ~/.zshrc

Then restart Claude Code so it picks up the new variable.

Tell [Partner 2 name] to do the same on her machine with the same token —
she'll need it to see the shared memory too.

Come back and run /init once restarted — I'll verify and finish the setup.
```

### Step 4: Verify connection + auto-create sub-pages

If NOTION_API_KEY is set, attempt to list Notion pages using the MCP.

If successful:
- Automatically create the 7 sub-pages inside "Couple OS Memory":
  - Past Dates
  - Past Trips
  - Learnings
  - Wishlist
  - Memory Jar
  - Streak
  - Vibe Check History
- Populate each with the correct table/list structure matching local markdown files

Then say:
```
Connected. I've created all 7 memory pages inside "Couple OS Memory":
✓ Past Dates
✓ Past Trips
✓ Learnings
✓ Wishlist
✓ Memory Jar
✓ Streak
✓ Vibe Check History

**Setup complete.** From now on:
- Every /feedback, /remember, /memory-jar update saves to Notion
- Both you and [Partner 2 name] see the same memory
- Local markdown files stay as backup

One last thing — share the workspace with [Partner 2 name]:
1. Open "Couple OS Memory" in Notion
2. Click "Share" (top right)
3. Invite [Partner 2 name]'s email with "Editor" access
4. Do NOT enable "Share to web" — keep it private between you two

Your shared memory is live.
```

If connection failed:
```
I can see the API key but can't reach your pages. Common fixes:
1. Make sure you connected "Couple OS" to the page (Step 2, items 7-10)
2. Make sure the token is correct (starts with secret_)
3. Try restarting Claude Code one more time

Want to try again?
```

### Step 5: Record page IDs

After successful connection, read the Notion pages and save their IDs
to sync/notion-setup.md in the Page IDs section.

Say:
```
Page IDs saved. You won't need to think about these — 
the system uses them automatically.
```

## Tone

- Friendly, practical, patient
- Number every step clearly
- Wait for confirmation between steps — never rush ahead
- If they get stuck, troubleshoot before suggesting they start over
