# Gmail Triage

Triage your email inbox — classify, prioritize, and take action. Requires Gmail connected via MCP.

---

## Setup Required

This command requires a Gmail MCP integration. Options:
- **[Rube](https://www.tryrube.com/)** — managed MCP gateway with Gmail toolkit (easiest)
- **Google's official MCP server** — [github.com/anthropics/claude-code/blob/main/docs/mcp.md](https://docs.anthropic.com/en/docs/claude-code/mcp)
- **Any MCP server** that exposes Gmail search, read, label, and draft tools

Once connected, replace the tool references below with your actual MCP tool names.

---

## 1. Fetch Inbox

Fetch all messages currently in the inbox:
- Query: `in:inbox`
- Extract: message ID, thread ID, from, subject, snippet, date
- If your Gmail tool supports pagination, paginate until all messages are fetched

**Deduplication (optional):** Read `.gmail-triaged-ids` to skip emails already triaged in a previous run. If the file doesn't exist, process everything.

If the inbox is empty or all emails were already triaged, say **"Inbox is clean — nothing to triage."** and skip to Step 7.

## 2. Mark All as Read

Mark all fetched messages as read (remove `UNREAD` label) so notifications stop buzzing.

## 3. Classify & Label

Using sender, subject, and snippet, classify each email into a label category. Customize these to match your work:

| Label | What goes here |
|-------|---------------|
| Work | Direct work emails — team, manager, clients |
| Finance | Invoices, banking, accounting, expenses |
| Legal | Contracts, compliance, legal correspondence |
| HR / People | Team HR, hiring, recruiting, benefits |
| Calendar | Meeting invites, schedule changes |
| Product | Product updates, feature requests, bug reports |
| Sales | Sales pipeline, deals, customer outreach |
| Marketing | Campaigns, analytics, brand |
| Newsletters | Subscriptions, digests, content |
| Misc | Everything else |

**To customize:** Create these labels in Gmail, then map their label IDs here. You can find label IDs using your MCP tool's list-labels endpoint.

Apply labels in batch (one call per label group) for efficiency.

## 4. Prioritize

Assign each email a priority tier:

### High Priority — needs your action
- From your boss, co-founders, leadership, board, investors
- From direct reports requesting decisions
- Emails explicitly requesting a reply or decision from you
- Time-sensitive content (deadlines, urgent language)

### Medium Priority — should read, may need action
- From team members (updates, non-urgent requests)
- External contacts (partners, clients)
- Threads where you're in TO (not just CC)
- Calendar and meeting related

### Low Priority — informational, can archive
- Newsletters, marketing, automated notifications
- CC'd threads where you don't need to act
- System notifications (GitHub, Linear, Slack digests)
- Promotional emails

**Customize the priority rules** to match your org. Add your leadership team's emails, key clients, etc.

## 5. Present Prioritized Inbox

Show a table grouped by priority:

```
## High Priority (X emails) — need your action
| # | From | Subject | Label | Action needed |
|---|------|---------|-------|---------------|

## Medium Priority (X emails) — read when you can
| # | From | Subject | Label |
|---|------|---------|-------|

## Low Priority (X emails) — will archive on your OK
| # | From | Subject | Label |
|---|------|---------|-------|
```

Ask: **"Does this prioritization look right? Say OK to proceed, or tell me what to move."**

## 6. Take Action (on user's OK)

### Low priority
- Archive all (remove `INBOX` label)

### High priority
- For each email needing a reply:
  1. Fetch the full message
  2. Draft a reply matching the sender's language and tone
  3. Save as draft in Gmail
- Show a summary of all drafts created

### Medium priority
- Leave in inbox for manual review

Close with: **"Done. X low-priority archived. X drafts created. Open Gmail to review and send."**

## 7. Save Triaged IDs

Append all processed message IDs to `.gmail-triaged-ids` (one per line) so the next run skips them.

If the file exceeds 500 lines, trim the oldest half.
