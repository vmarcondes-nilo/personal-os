# Morning Brief

Run the daily morning brief. Follow every step below in order.

## 1. Read Context

Read these files to build today's context:
- `inbox.md` — capture items to process
- Current quarter's OKR file in `goals/`
- Yesterday's journal entry at `journal/daily/` (find the most recent file)
- Relevant area files in `areas/`

## 2. Fetch External Data (Optional)

If you've connected MCP integrations, pull in live data. Skip any that aren't configured.

**Calendar** (Google Calendar, Outlook, etc.):
- Fetch today's events from your primary calendar
- Flag meetings that need prep
- Note gaps in the schedule for deep work

**Tasks** (Trello, Todoist, Linear, Google Tasks, etc.):
- Fetch open tasks from your active list
- Include them in the priorities review below

**Email** (Gmail, Outlook, etc.):
- Fetch unread count and any high-priority senders
- If there are many unreads, suggest running `/gmail` after the brief

**Meeting notes** (via `/meetsync`):
- Check `meetings/.last-sync` — if yesterday's meetings haven't been processed, suggest running `/meetsync`
- If recent meeting notes exist, scan for open action items

## 3. Process Inbox

For each item in `inbox.md`:
- Route actionable items to the appropriate area file, goals, decisions, or people tracker
- Tell the user what you routed and where
- Leave unprocessed items in place; clear the processed ones

## 4. Check Important Dates

Check if any key dates fall within the next 7 days:
- Reference dates from `CLAUDE.md` and `profile/family.md`
- Also check for any deadlines in OKRs or area files

## 5. Present Summary

Give a concise morning snapshot:
- **Inbox items** processed (or flagged for discussion)
- **Upcoming dates** (next 7 days)
- **Current priorities** from areas and goals
- **Yesterday's carryover** (anything unfinished from last journal entry)

## 6. Ask for Today's Top 3

Ask: **"What are your top 3 priorities for today?"**

Coaching rules:
- Max 3 — push back if they try to add more
- Challenge: are these truly important, or just urgent?
- Check alignment with weekly/quarterly goals
- If overcommitting, say so directly

## 7. Coaching Nudge

Rotate through one of these themes (pick whichever hasn't come up recently based on journal history):
- **Work prompt**: A strategic question to sit with during the day
- **Relationship reminder**: Something for partner, kids, or a friend
- **Health check**: "Did you exercise yesterday? What's the plan today?"
- **Energy check**: "How are you sleeping? What's your energy level?"

## 8. Save & Close

Write the brief to `journal/daily/YYYY-MM-DD.md` using today's date:

```markdown
# Daily Brief — YYYY-MM-DD

## Inbox Processed
- (items routed)

## Today's Calendar
- (meetings and commitments, or "No calendar integration configured")

## Upcoming Dates
- (if any in next 7 days)

## Today's Top 3
1.
2.
3.

## Coaching Nudge
- (the prompt or reminder)

## Notes
- (anything discussed)
```

After saving, confirm that the journal entry was written.
