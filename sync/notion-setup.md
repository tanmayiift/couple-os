# Notion Shared Memory Setup

The easiest way to do this is to run `/init` inside Claude Code — it walks you
through every step interactively and creates the pages for you automatically.

If you prefer to set it up manually, follow the steps below.

---

## What you do vs what Claude does

**You do (requires a browser, ~10 minutes):**
- Create a Notion account (free)
- Create one top-level page: "Couple OS Memory"
- Create the integration and copy the token
- Connect the integration to your page
- Add the token to your shell profile

**Claude does automatically once connected:**
- Creates all 7 sub-pages with the right structure
- Populates them as you use /feedback, /remember, etc.
- Keeps local markdown files as backup

You do NOT need to create the sub-pages manually.

---

## Privacy

Pages should be **private, not public.**

Share only with your partner:
- Open "Couple OS Memory" in Notion
- Click "Share" → Invite your partner's email → Editor access
- Do NOT enable "Share to web"

The 5 core profile files (couple-profile, preferences, financials, constraints,
local-context) never sync to Notion — they stay local only.
/surprise outputs never sync either — ever.

---

## Manual Setup Steps

### 1. Create the workspace page

1. Go to [notion.so](https://notion.so) and sign in (or create a free account)
2. Create a new top-level page called **"Couple OS Memory"**

Don't create sub-pages — Claude will create them automatically.

### 2. Create the integration

1. Go to [notion.so/my-integrations](https://notion.so/my-integrations)
2. Click "+ New integration"
3. Name it: **"Couple OS"**
4. Select your workspace
5. Click "Submit"
6. Copy the **Internal Integration Secret** (starts with `secret_`)

### 3. Connect the integration to your page

1. Go back to "Couple OS Memory" in Notion
2. Click the **···** menu (top right)
3. Click **"Add connections"**
4. Search for "Couple OS" and select it

### 4. Add the token to your shell

Run this in your terminal:

```bash
echo 'export NOTION_API_KEY="your_secret_token_here"' >> ~/.zshrc
source ~/.zshrc
```

For bash users, replace `~/.zshrc` with `~/.bashrc`.

Share the same token with your partner — they run the same command on their machine.

### 5. Restart Claude Code and verify

Restart Claude Code, then run:

```
/init
```

Claude will verify the connection and automatically create all 7 sub-pages.

---

## What gets synced

| Local file | Notion page | Syncs? |
|-----------|-------------|--------|
| memory/past-dates.md | Past Dates | ✓ |
| memory/past-trips.md | Past Trips | ✓ |
| memory/learnings.md | Learnings | ✓ |
| memory/wishlist.md | Wishlist | ✓ |
| memory/memory-jar.md | Memory Jar | ✓ |
| memory/streak.md | Streak | ✓ |
| memory/vibe-check-history.md | Vibe Check History | ✓ |
| couple-profile.md | — | ✗ local only |
| preferences.md | — | ✗ local only |
| financials.md | — | ✗ local only |
| constraints.md | — | ✗ local only |
| local-context.md | — | ✗ local only |
| outputs/surprises/ | — | ✗ local only |

---

## Page IDs (auto-populated by /init)

After setup, Claude saves these automatically. For reference:

- Past Dates page ID: _______________
- Past Trips page ID: _______________
- Learnings page ID: _______________
- Wishlist page ID: _______________
- Memory Jar page ID: _______________
- Streak page ID: _______________
- Vibe Check History page ID: _______________
