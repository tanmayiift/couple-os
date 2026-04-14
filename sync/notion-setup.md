# Notion Shared Memory Setup

Both partners complete this once. Takes 15 minutes.

## What Notion pages to create

One partner creates a free Notion account and workspace, then creates:

Page: "Couple OS Memory" (top level)
  └── Sub-page: "Past Dates"
  └── Sub-page: "Past Trips"  
  └── Sub-page: "Learnings"
  └── Sub-page: "Wishlist"
  └── Sub-page: "Memory Jar"
  └── Sub-page: "Streak"
  └── Sub-page: "Vibe Check History"

Share the workspace with your partner: Share → Invite → Editor access.

## Create a Notion Integration

1. Go to notion.so/my-integrations
2. Click "New Integration"
3. Name: "Couple OS"
4. Select your workspace
5. Copy the Integration Token (starts with secret_)
6. Go back to your Couple OS Memory page
7. Click ··· menu → Add connections → select "Couple OS"
8. Share the token with your partner over WhatsApp

## Connect Claude Code (both partners)

Add to your shell profile (~/.zshrc or ~/.bashrc):
```
export NOTION_API_KEY="paste_your_token_here"
```

Then run:
```
source ~/.zshrc
claude mcp add notion
```

## Verify connection

In Claude Code, type:
```
What Notion pages do I have access to?
```

Claude should list your Couple OS Memory pages.

## Page IDs

After connecting, Claude will auto-detect page IDs.
You can also find them in the page URL:
notion.so/Your-Page-Name-[THIS-IS-THE-ID]

Save your page IDs here after setup:
- Past Dates page ID: _______________
- Past Trips page ID: _______________
- Learnings page ID: _______________
- Wishlist page ID: _______________
- Memory Jar page ID: _______________
- Streak page ID: _______________
- Vibe Check History page ID: _______________
