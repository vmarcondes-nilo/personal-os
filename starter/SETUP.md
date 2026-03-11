# Personal OS — Setup Guide

No coding required. Just follow these steps.

---

## What you'll get

A personal operating system running in your terminal — daily briefs, weekly reviews, coaching sessions, decision logging, and life area tracking. All powered by AI, all stored as simple text files you own.

## Step 1: Install Claude Code

Claude Code is a command-line tool by Anthropic. You need it to run this system.

**On Mac:**
```bash
brew install claude-code
```

**On any system with npm:**
```bash
npm install -g @anthropic-ai/claude-code
```

If you don't have npm, install [Node.js](https://nodejs.org/) first (download the LTS version and install it — npm comes included).

After installing, run `claude` once in your terminal to authenticate with your Anthropic account.

Full install docs: https://docs.anthropic.com/en/docs/claude-code

## Step 2: Create your folder

Open your terminal and run:

```bash
mkdir personal-os
cd personal-os
```

This creates an empty folder where your system will live.

## Step 3: Add the CLAUDE.md file

Download the `CLAUDE.md` file from this folder and put it inside your `personal-os` folder.

Or copy-paste: open the `CLAUDE.md` file in this directory, copy the entire contents, and save it as `CLAUDE.md` inside your `personal-os` folder.

Your folder should now look like:
```
personal-os/
└── CLAUDE.md
```

## Step 4: Let Claude build your system

Open your terminal, navigate to the folder, and start Claude:

```bash
cd personal-os
claude
```

Then type this prompt:

> **"Set up my personal OS. Read the CLAUDE.md file and create the full system — all directories, templates, and slash commands. Then walk me through filling in my profile."**

Claude will:
1. Read the CLAUDE.md instructions
2. Create all the folders and template files
3. Create the slash commands (morning brief, weekly review, coaching, decisions)
4. Ask you questions to fill in your profile, values, family context, and goals

This takes about 5-10 minutes. Just answer Claude's questions.

## Step 5: Start using it

Once setup is complete, you can start using the system. Open Claude in your folder anytime:

```bash
cd personal-os
claude
```

### Daily commands

| What to type | What it does |
|-------------|-------------|
| `/morning` | Run your morning brief — process inbox, set priorities, get a coaching nudge |
| `/weekly` | Weekly review — score your life areas, celebrate wins, plan next week |
| `/decide` | Think through a tough decision with structured frameworks |
| `/coaching` | Deep coaching session on any problem |

### Natural language

You can also just talk naturally:

- "I need to think through whether to take this new job offer"
- "Update my health area — I started running this week"
- "What's on my plate this week?"
- "Add my friend Sarah to the people tracker"

### The inbox

Between sessions, drop thoughts, todos, and ideas into the `inbox.md` file. Your morning brief will process them.

You can edit `inbox.md` with any text editor, or just tell Claude:

> "Add to inbox: call dentist, review Q2 budget, look into that podcast Maria recommended"

## Step 6: Save your progress (optional but recommended)

If you want to keep a history of your evolution, initialize git:

```bash
cd personal-os
git init
git add -A
git commit -m "Initial setup"
```

After each session, save your changes:

```bash
git add -A
git commit -m "Daily brief 2025-03-11"
```

Or just ask Claude: "commit my changes".

## Tips

- **Morning brief is the most important ritual.** Try to do it every workday.
- **Don't skip weekly reviews.** Even 10 minutes is better than zero.
- **Be honest in your profile.** The more context Claude has, the better the coaching.
- **Use inbox.md aggressively.** Dump everything there — the morning brief sorts it.
- **Voice input works great.** Tools like Wispr Flow or macOS Dictation let you talk to Claude naturally.

## Advanced: Connect external tools

Once you're comfortable with the basics, you can connect external tools to make the system even more powerful:

- **Gmail** — AI email triage with `/gmail`
- **Google Calendar** — today's schedule in your morning brief
- **Google Meet** — auto-process meeting transcripts with `/meetsync`
- **Trello / Todoist / Google Tasks** — task sync

This requires MCP (Model Context Protocol) setup. See the main [README](../README.md) for details, or use [Rube](https://www.tryrube.com/) for the easiest setup.

---

## Troubleshooting

**"Command not found: claude"**
- Make sure Claude Code is installed. Run `npm install -g @anthropic-ai/claude-code` and try again.

**"Claude doesn't seem to know about the system"**
- Make sure the `CLAUDE.md` file is in the same folder where you're running `claude`. It reads this file automatically.

**"I messed something up"**
- If you set up git, you can undo: `git checkout .`
- If not, just tell Claude: "Reset my system — recreate all templates from CLAUDE.md"

**"I want to start over"**
- Delete the folder and redo from Step 2. Your CLAUDE.md file is the blueprint — everything else can be regenerated.
