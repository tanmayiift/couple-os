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

**Step 1: Create the Notion pages**

1. Go to notion.so and sign in (or create a free account)
2. Create a new top-level page called "Couple OS Memory"
3. Inside that page, create these 7 sub-pages:
   - Past Dates
   - Past Trips
   - Learnings
   - Wishlist
   - Memory Jar
   - Streak
   - Vibe Check History

Just blank pages for now — I'll populate them.

Tell me when you've created all 7 pages.
```

Wait for confirmation before proceeding.

### Step 2: Share with partner

Say:
```
**Step 2: Share with [Partner 2 name]**

On the "Couple OS Memory" page:
1. Click "Share" in the top right
2. Invite [Partner 2 name]'s email with "Editor" access
3. She'll get an invite to join the workspace

Done? Let's set up the integration next.
```

Wait for confirmation.

### Step 3: Create the Notion integration

Say:
```
**Step 3: Create the API integration**

This lets Claude Code read and write to your Notion pages.

1. Go to notion.so/my-integrations
2. Click "+ New integration"
3. Name it: "Couple OS"
4. Select your workspace
5. Click "Submit"
6. You'll see an "Internal Integration Secret" — copy it (starts with `secret_`)

Now connect it to your pages:
7. Go back to your "Couple OS Memory" page in Notion
8. Click the ··· menu (top right)
9. Click "Add connections"
10. Search for "Couple OS" and select it

Paste the secret token here when you're ready (I won't store it in any file —
it goes straight to your shell profile).
```

Wait for the token.

### Step 4: Save the API key

When they paste the token, verify it starts with `secret_`.

Say:
```
**Step 4: Save to your shell**

Run this in your terminal (outside Claude Code):

```
echo 'export NOTION_API_KEY="[THEIR_TOKEN]"' >> ~/.zshrc
source ~/.zshrc
```

Then restart Claude Code so it picks up the new environment variable.

Tell [Partner 2 name] to do the same on her machine with the same token.

Come back and type /init after restarting — I'll verify the connection.
```

### Step 5: Verify connection

If NOTION_API_KEY is set, attempt to list Notion pages using the MCP.

If successful:
```
Connected. I can see your Couple OS Memory pages:
[list the pages found]

**Setup complete.** From now on:
- Every /feedback, /remember, /memory-jar update saves to Notion
- Both you and [Partner 2 name] see the same memory
- Local markdown files stay as backup

Your shared memory is live.
```

If failed:
```
I can see the API key but can't reach your pages. Common fixes:
1. Make sure you added the "Couple OS" connection to the page (Step 3, items 7-10)
2. Make sure the token is correct (starts with secret_)
3. Try restarting Claude Code one more time

Want to try again?
```

### Step 6: Record page IDs

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
