# Daily Brief Template

**Duration**: 5-10 minutes
**When**: Morning, ideally before deep work starts
**Output**: Saved to `journal/daily/YYYY-MM-DD.md`

---

## Script for Claude

When the user asks for a "morning brief" or "daily brief", follow these steps:

### 1. Process Inbox (1 min)
- Read `inbox.md`
- For each item: route to the appropriate area file, goals, decisions, or people tracker
- Clear processed items from inbox (leave unprocessed ones)
- Tell the user what you routed and where

### 2. Check Calendar & Tasks (1 min)
<!-- OPTIONAL: If you've connected Google Calendar, Trello, Todoist, etc. via MCP, add fetch steps here -->
- Review any task management system for today's items
- Check calendar for today's meetings and commitments
- Flag anything that needs prep

### 3. Check Important Dates (30 sec)
- Check if any key dates are coming up in the next 7 days (birthdays, anniversaries, deadlines)
- Reference dates from `CLAUDE.md` and `profile/family.md`
- Alert the user to anything upcoming

### 4. Review Priorities (2 min)
- Read active priorities from relevant `areas/` files
- Read current OKRs from `goals/`
- Read yesterday's journal entry if it exists
- Summarize: "Here's where you are and what matters today"

### 5. Today's Focus (2 min)
Ask: **"What are your top 3 priorities for today?"**
- Help narrow to the truly important (not just urgent)
- Challenge if overcommitting — 3 is the max
- Check alignment with weekly/quarterly goals

### 6. Coaching Nudge (1 min)
One of these, rotating:
- **Work prompt**: A strategic question to sit with during the day
- **Relationship reminder**: Something for partner, kids, or a friend
- **Health check**: "Did you exercise yesterday? What's the plan today?"
- **Energy check**: "How are you sleeping? What's your energy level?"

### 7. Save & Close
- Write the brief output to `journal/daily/YYYY-MM-DD.md`
- Format:

```markdown
# Daily Brief — YYYY-MM-DD

## Inbox Processed
- (items routed)

## Today's Calendar
- (meetings and commitments)

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
