# Weekly Review Template

**Duration**: 20-30 minutes
**When**: Sunday evening or Monday morning
**Output**: Saved to `journal/weekly/YYYY-WNN.md`

---

## Script for Claude

When the user asks for a "weekly review", follow these steps:

### 1. Look Back (5 min)
- Read this week's daily journal entries from `journal/daily/`
- Read current state of all `areas/` files
- Summarize: what happened this week across all areas

### 2. Score Each Area (5 min)
Ask the user to rate each area 1-10 for the week:

| Area | Score | Why |
|------|-------|-----|
| Work | /10 | |
| Relationships | /10 | |
| Health | /10 | |
| Personal Growth | /10 | |

Discuss: Which area needs the most attention next week?

### 3. Wins & Gratitude (3 min)
Ask:
- **"What are you most proud of this week?"** (at least 1 win)
- **"What are you grateful for?"**

### 4. Lessons & Gaps (3 min)
Ask:
- **"What didn't go well? What fell through the cracks?"**
- **"What would you do differently?"**
- **"Any commitments you didn't keep?"**

### 5. Next Week's Priorities (5 min)
For each area, set 1-2 priorities for next week:
- **Work**: What's the #1 thing to move forward?
- **Relationships**: Who needs your attention?
- **Health**: What's the exercise/sleep plan?
- **Personal Growth**: What will you learn or build?

### 6. OKR Check (3 min)
- Review current quarter's OKR file in `goals/`
- Update progress on key results
- Flag any that are at risk

### 7. Process & Update (3 min)
- Process any remaining `inbox.md` items
- Update `areas/` files with new information
- Update `goals/` with progress
- Log any pending decisions

### 8. Save
Write review to `journal/weekly/YYYY-WNN.md`:

```markdown
# Weekly Review — YYYY-WNN

## Area Scores
| Area | Score | Notes |
|------|-------|-------|
| Work | /10 | |
| Relationships | /10 | |
| Health | /10 | |
| Personal Growth | /10 | |

## Wins
-

## Gratitude
-

## Lessons / What Fell Through
-

## Next Week's Priorities
- **Work**:
- **Relationships**:
- **Health**:
- **Personal Growth**:

## OKR Progress
- (updates)

## Notes
- (anything else discussed)
```
