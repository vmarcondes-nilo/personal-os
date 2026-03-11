# Decision Logger

Help think through and log an important decision. This is a structured coaching conversation that ends with a saved decision record.

**Topic**: $ARGUMENTS

---

## 1. Read Context

Read these files for background:
- `decisions/_template.md` — output format
- Current quarter's OKR file in `goals/` — decisions should align with goals
- Relevant area file in `areas/`
- Recent entries in `decisions/` — to see past decisions and avoid revisiting settled ones

## 2. Clarify the Decision

If `$ARGUMENTS` is provided, use it as the starting point. Otherwise ask: **"What decision are you wrestling with?"**

Then clarify:
- **"What's forcing this decision now?"** — understand the trigger and urgency
- **"What happens if you do nothing?"** — check if it even needs deciding today
- **Area**: Which life area does this touch?

Keep this tight — 2-3 questions max. Don't over-interview.

## 3. Map Options

Ask: **"What options are you considering?"**

Let the user go first, then:
- Add options they might be missing (there's almost never just 2)
- For each option, briefly note:
  - **Upside**: best realistic outcome
  - **Downside**: worst realistic outcome
  - **Reversibility**: easy to undo, or a one-way door?

## 4. Pressure-Test

Pick the right lens for this decision:

**Strategic decisions** (company, product, hiring):
- Pre-mortem: "It's 6 months later and this failed — what went wrong?"
- First principles: "What assumptions are baked in here?"

**Resource decisions** (time, money, priorities):
- "What are you saying no to by saying yes to this?"
- 80/20: "Which option gets 80% of the result with 20% of the effort?"

**Personal decisions** (family, health, lifestyle):
- "What will you regret NOT doing?"
- "What aligns with your values?" (reference `profile/values.md`)
- "What would you tell a friend in this situation?"

Be direct. Challenge weak reasoning. Don't just validate — push back.

## 5. Decide

Push for a clear outcome:
- **"What are you going to do?"**
- **"By when?"**
- **"Who needs to know?"**
- **"What's the first concrete action?"**

If not ready to decide, that's OK — set a review date and note what's missing.

## 6. Save the Decision

Save to `decisions/YYYY-MM-DD-short-title.md` using the template from `decisions/_template.md`.

## 7. Update System

- If the decision affects an area, update the relevant `areas/` file
- If it creates action items, add them to `inbox.md`
- If it involves people, update relevant `people/` files
- Confirm what was saved and where
