# Meeting Sync

Process meeting transcripts into structured notes and action items. Requires Google Calendar and Google Docs connected via MCP.

---

## Setup Required

This command requires MCP integrations for:
1. **Google Calendar** — to fetch events and find transcript attachments
2. **Google Docs** — to read the transcript content

Options:
- **[Rube](https://rube.app/)** — managed MCP gateway with Google Calendar + Docs toolkits
- **Google's official MCP servers** — see [Claude Code MCP docs](https://docs.anthropic.com/en/docs/claude-code/mcp)

**How transcripts work:** If you use Google Meet with Gemini note-taking enabled, Google auto-attaches a summary doc to the calendar event after the meeting. This command finds those docs and processes them. The attachment title varies by language (e.g., "Gemini notes" in English, "Anotações do Gemini" in Portuguese).

If you use a different transcription tool (Otter, Fireflies, etc.), adapt Step 3 to find transcripts wherever your tool stores them.

---

## 1. Determine Date Range

Read `meetings/.last-sync` to find the last processed date.
- If the file exists: fetch events from **the day after last sync** through **yesterday**
- If the file does not exist: default to the **last 48 hours**

## 2. Fetch Calendar Events

Fetch calendar events for the date range:
- Use your calendar MCP tool with the determined time range
- Set timezone to your local timezone
- Only query your primary calendar (not shared/subscribed calendars) to avoid noise

## 3. Identify Events with Transcripts

**Step 3a — Filter to real meetings:**
- Skip all-day events
- Skip cancelled events
- Only keep events with a video conferencing link (Google Meet, Zoom, etc.)

**Step 3b — Check for transcript attachments:**
For each remaining meeting, check for attached documents:
- **Google Meet + Gemini**: Look for a Google Doc attachment (title varies by language — "Gemini notes", "Anotações do Gemini", etc.)
- **Other tools**: Adapt this check based on where your transcription tool saves output

Parallelize these checks where possible for speed.

Skip events with no transcript attachment.

## 4. Fetch Transcript Content

For each transcript found:
- Extract the document ID from the attachment
- Fetch the full text content via your Google Docs MCP tool
- Batch all fetches in parallel for efficiency

## 5. Process Each Transcript

For each meeting with a transcript, extract:

- **Summary**: 3-5 bullet points capturing the essence
- **Key decisions**: Any decisions made during the meeting
- **Action items**: Tasks with owners and deadlines if mentioned
- **Context updates**: Anything relevant for `areas/` or `people/` files

## 6. Save Structured Notes

Write each meeting to `meetings/notes/YYYY-MM-DD-meeting-title.md`:

```markdown
# Meeting: [Title]
**Date:** YYYY-MM-DD
**Attendees:** [list from calendar event]
**Type:** [1:1 / team sync / standup / strategy / external]

## Summary
- (3-5 bullet points)

## Key Decisions
- (if any)

## Action Items
- [ ] [Owner]: [action] — [deadline if mentioned]

## Raw Transcript
<details>
<summary>Full transcript</summary>
(full text here)
</details>
```

Use lowercase-kebab-case for the meeting title in the filename.

## 7. Update System Files

If transcripts reveal relevant updates:
- Update appropriate `areas/` files with new information
- Update `people/` files with 1:1 context or commitments
- Add action items to `inbox.md` if they need follow-up

Only update when there's genuinely new, meaningful information.

## 8. Update Last Sync

Write yesterday's date (YYYY-MM-DD) to `meetings/.last-sync`.

## 9. Show Summary

Present a concise summary:
- Number of meetings processed
- For each: title, date, number of action items
- Consolidated action items across all meetings
- Any system file updates made

If no meetings with transcripts were found: **"No meetings with transcripts found for [date range]."**
