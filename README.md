# personal-os

A markdown-based personal operating system powered by [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

Your AI chief of staff — daily briefs, weekly reviews, coaching sessions, decision logging, and life area tracking. All in plain text files you own.

## What is this?

This is a system of markdown files + Claude Code slash commands that turns your terminal into a personal executive assistant and life coach. It:

- **Runs your morning brief** — processes your inbox, reviews priorities, sets your top 3 for the day
- **Facilitates weekly reviews** — scores life areas, celebrates wins, plans next week
- **Coaches you through decisions** — structured frameworks, pressure-testing, and a decision log
- **Tracks your life areas** — work, relationships, health, personal growth
- **Manages goals** — annual themes and quarterly OKRs with progress tracking
- **Remembers context** — people, values, key dates, and what matters to you

Everything is stored as plain markdown files in a git repo. No lock-in, no SaaS, fully portable.

## Quick Start

### Option A: Non-technical setup (no git required)

If you're not comfortable with git/GitHub, use the **[starter kit](starter/)**:
1. Download the two files from the `starter/` folder (`CLAUDE.md` and `SETUP.md`)
2. Follow the step-by-step instructions in `SETUP.md`
3. Claude will build the entire system for you from the CLAUDE.md file

### Option B: Clone this repo (recommended for developers)

#### Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed and authenticated
- Git

#### Setup

```bash
# Clone the repo
git clone https://github.com/vmarcondes-nilo/personal-os.git
cd personal-os

# Fill in your profile
# Edit these files with your information:
#   profile/me.md      — who you are
#   profile/family.md   — your family context
#   profile/values.md   — your core values
#   profile/company.md  — your work context (optional)
#   CLAUDE.md           — update the "Who You're Working With" section

# Set your goals
#   goals/2025-annual.md — your annual goals
#   goals/2025-Q1.md     — this quarter's OKRs

# Start using it
claude
```

#### Your First Session

Open Claude Code in the repo directory and try:

```
/morning          # Run your daily brief
/weekly           # Run your weekly review
/decide           # Think through a decision
/coaching         # Start a coaching session
/gmail            # Triage your inbox (requires MCP setup)
/meetsync         # Process meeting transcripts (requires MCP setup)
```

Or just talk to it naturally:

```
> "I need to think through whether to take this new job offer"
> "Update my health area — I started running this week"
> "What's on my plate this week?"
```

## Directory Structure

```
personal-os/
├── CLAUDE.md                    # System instructions (Claude reads this automatically)
├── inbox.md                     # Quick capture — drop thoughts here between sessions
├── profile/
│   ├── me.md                    # Your identity and context
│   ├── family.md                # Family members and key dates
│   ├── values.md                # Core values and principles
│   └── company.md               # Work/company context (optional)
├── areas/
│   ├── work.md                  # Career and professional life
│   ├── relationships.md         # Partner, family, friends
│   ├── health.md                # Exercise, sleep, energy
│   └── personal-growth.md       # Learning, side projects, growth
├── goals/
│   ├── 2025-annual.md           # Annual goals and theme
│   └── 2025-Q1.md              # Quarterly OKRs
├── rituals/
│   ├── daily-brief.md           # Morning brief template
│   ├── weekly-review.md         # Weekly review template
│   ├── monthly-review.md        # Monthly review template
│   └── coaching-session.md      # Coaching session framework
├── decisions/
│   └── _template.md             # Decision log template
├── people/
│   └── _template.md             # Relationship tracker template
├── journal/
│   ├── daily/                   # Daily brief outputs (YYYY-MM-DD.md)
│   └── weekly/                  # Weekly review outputs (YYYY-WNN.md)
├── meetings/
│   └── notes/                   # Meeting notes (optional)
└── .claude/
    └── commands/
        ├── morning.md           # /morning slash command
        ├── weekly.md            # /weekly slash command
        ├── decide.md            # /decide slash command
        ├── coaching.md          # /coaching slash command
        ├── gmail.md             # /gmail slash command (requires MCP)
        └── meetsync.md          # /meetsync slash command (requires MCP)
```

## How It Works

### The Core Loop

1. **Capture**: Drop thoughts, todos, and ideas into `inbox.md` anytime
2. **Process**: Each morning brief routes inbox items to the right place
3. **Review**: Weekly reviews score your life areas and plan ahead
4. **Decide**: Major decisions get structured analysis and a permanent record
5. **Track**: Areas, goals, and people files build context over time

### Slash Commands

| Command | What it does |
|---------|-------------|
| `/morning` | Morning brief — process inbox, review priorities, set top 3, coaching nudge |
| `/weekly` | Weekly review — score areas, celebrate wins, plan next week, update OKRs |
| `/decide [topic]` | Decision logger — structured framework to think through and record decisions |
| `/coaching [topic]` | Coaching session — deep-dive on any problem using proven frameworks |
| `/gmail` | Email triage — classify, prioritize, archive low-priority, draft replies (requires MCP) |
| `/meetsync` | Meeting sync — process transcripts into structured notes and action items (requires MCP) |

### Life Areas

The system tracks four default areas (customize these to match your life):

- **Work** — career, company, projects, professional development
- **Relationships** — partner, family, friends, social life
- **Health** — exercise, sleep, nutrition, energy, mental health
- **Personal Growth** — learning, side projects, skills, hobbies

Each area file tracks current state, active goals, and a weekly review section.

### Coaching Frameworks

When you need to think through something, Claude uses these frameworks:

- **First Principles** — strip assumptions, find what's actually true
- **Pre-mortem** — "it failed in 6 months — why?"
- **Eisenhower Matrix** — urgent vs. important
- **80/20** — what 20% of effort gets 80% of results?
- **Inversion** — what would guarantee failure? Now avoid that.

## Customization

### Add Your Own Areas

Create new files in `areas/` for any life domain you want to track:

```bash
# Examples
areas/finances.md
areas/parenting.md
areas/side-project.md
areas/spirituality.md
```

Update the weekly review template in `rituals/weekly-review.md` to include your new areas.

### Add Your Own Slash Commands

Create `.md` files in `.claude/commands/` to add new workflows:

```bash
# Examples
.claude/commands/journal.md      # Free-form journaling session
.claude/commands/prep.md         # Meeting preparation workflow
.claude/commands/retro.md        # Sprint/project retrospective
```

### Connect External Tools (Advanced)

Claude Code supports [MCP (Model Context Protocol)](https://modelcontextprotocol.io/) integrations. Two commands — `/gmail` and `/meetsync` — are built to use MCP out of the box. The `/morning` brief also pulls in live data when integrations are available.

**Recommended integrations:**

| Integration | Unlocks | Used by |
|-------------|---------|---------|
| **Gmail** | Email triage, drafting replies, archiving | `/gmail`, `/morning` |
| **Google Calendar** | Today's schedule, meeting prep flags | `/morning`, `/meetsync` |
| **Google Docs** | Reading meeting transcripts (Gemini notes) | `/meetsync` |
| **Trello / Todoist / Linear / Google Tasks** | Task sync in morning brief | `/morning` |
| **Slack** | Message summaries | Custom commands |

**How to connect:**
1. **Easiest**: Use [Rube](https://www.tryrube.com/) — a managed MCP gateway that handles OAuth and exposes tools for Gmail, Calendar, Docs, Trello, and more
2. **DIY**: Set up individual MCP servers — see the [Claude Code MCP docs](https://docs.anthropic.com/en/docs/claude-code/mcp)

Each command file (`.claude/commands/gmail.md`, `meetsync.md`) includes setup instructions and explains which MCP tools are needed.

## Philosophy

This system is built on a few beliefs:

1. **Plain text is forever** — markdown files in a git repo will outlast any app
2. **Context is everything** — the more Claude knows about you, the better it helps
3. **Structure enables freedom** — rituals and templates reduce decision fatigue
4. **Review beats planning** — the weekly review is the most important ritual
5. **You own your data** — everything lives on your machine, in files you control

## Tips

- **Use `inbox.md` aggressively** — dump everything there between sessions. Your morning brief will sort it.
- **Be honest in your profiles** — Claude can only help with what it knows. The more context you give, the better the coaching.
- **Don't skip weekly reviews** — they're the heartbeat of the system. Even a 10-minute review beats no review.
- **Customize the areas** — the defaults are a starting point. Add, rename, or remove areas to match your life.
- **Commit regularly** — `git commit` after each session to keep a history of your evolution.
- **Voice input works great** — tools like Wispr Flow or macOS Dictation let you talk to Claude naturally.

## Privacy

This repo is designed to be private by default. If you want to share your setup:

- Never commit secrets, credentials, or API keys
- Review `profile/` files before making the repo public
- Use `.gitignore` to exclude sensitive directories (journal, decisions, etc.)

---

## Leia em Português

<details>
<summary><strong>🇧🇷 Versão em Português</strong></summary>

### O que é isso?

Um sistema operacional pessoal baseado em arquivos markdown, rodando no [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

Seu chefe de gabinete com IA — briefings diários, revisões semanais, sessões de coaching, registro de decisões e acompanhamento de áreas da vida. Tudo em arquivos de texto que são seus.

### Como funciona

É um repositório git com arquivos markdown + comandos slash do Claude Code que transformam seu terminal em um assistente executivo pessoal e coach de vida:

- **Briefing matinal** (`/morning`) — processa sua inbox, revisa prioridades, define o top 3 do dia
- **Revisão semanal** (`/weekly`) — avalia áreas da vida, celebra conquistas, planeja a próxima semana
- **Decisões** (`/decide`) — frameworks estruturados para pensar e registrar decisões importantes
- **Coaching** (`/coaching`) — sessão aprofundada sobre qualquer problema
- **Triagem de email** (`/gmail`) — classifica, prioriza, arquiva e rascunha respostas (requer MCP)
- **Sync de reuniões** (`/meetsync`) — processa transcrições em notas estruturadas e ações (requer MCP)

### Início rápido

**Não é técnico?** Use o [starter kit](starter/) — baixe dois arquivos, siga as instruções, e o Claude monta tudo pra você.

**Para desenvolvedores:** Clone o repo e preencha seus dados.

```bash
# Clone o repo
git clone https://github.com/YOUR_USERNAME/personal-os.git
cd personal-os

# Preencha seu perfil
# Edite estes arquivos com suas informações:
#   profile/me.md      — quem você é
#   profile/family.md   — contexto familiar
#   profile/values.md   — seus valores
#   profile/company.md  — contexto profissional (opcional)
#   CLAUDE.md           — atualize a seção "Who You're Working With"

# Defina suas metas
#   goals/2025-annual.md — metas anuais
#   goals/2025-Q1.md     — OKRs do trimestre

# Comece a usar
claude
```

### Estrutura de diretórios

| Diretório | Função |
|-----------|--------|
| `profile/` | Contexto estático — identidade, família, empresa, valores |
| `areas/` | Áreas da vida — trabalho, relacionamentos, saúde, crescimento pessoal |
| `goals/` | Metas anuais e OKRs trimestrais |
| `rituals/` | Templates de sessões recorrentes (diária, semanal, mensal, coaching) |
| `decisions/` | Registro de decisões importantes com raciocínio |
| `people/` | Tracker de relacionamentos importantes |
| `journal/` | Outputs de briefings diários e revisões semanais |
| `meetings/` | Notas de reuniões processadas |
| `inbox.md` | Captura rápida — pensamentos, tarefas, ideias |

### O loop principal

1. **Capturar**: Jogue pensamentos, tarefas e ideias no `inbox.md` a qualquer momento
2. **Processar**: O briefing matinal direciona cada item para o lugar certo
3. **Revisar**: Revisões semanais avaliam suas áreas e planejam a semana seguinte
4. **Decidir**: Decisões importantes recebem análise estruturada e registro permanente
5. **Acompanhar**: Arquivos de áreas, metas e pessoas acumulam contexto ao longo do tempo

### Integrações externas (avançado)

Os comandos `/gmail` e `/meetsync` usam integrações MCP. O `/morning` também puxa dados ao vivo quando disponíveis.

| Integração | O que desbloqueia | Usado por |
|------------|-------------------|-----------|
| **Gmail** | Triagem de email, rascunhos, arquivamento | `/gmail`, `/morning` |
| **Google Calendar** | Agenda do dia, alertas de preparo | `/morning`, `/meetsync` |
| **Google Docs** | Leitura de transcrições (Gemini) | `/meetsync` |
| **Trello / Todoist / Linear / Google Tasks** | Sync de tarefas no briefing | `/morning` |

**Como conectar:**
1. **Mais fácil**: Use o [Rube](https://www.tryrube.com/) — gateway MCP gerenciado que cuida do OAuth e expõe ferramentas para Gmail, Calendar, Docs, Trello e mais
2. **Faça você mesmo**: Configure servidores MCP individuais — veja a [documentação de MCP do Claude Code](https://docs.anthropic.com/en/docs/claude-code/mcp)

### Filosofia

1. **Texto puro é para sempre** — arquivos markdown num repo git duram mais que qualquer app
2. **Contexto é tudo** — quanto mais o Claude sabe sobre você, melhor ele ajuda
3. **Estrutura liberta** — rituais e templates reduzem fadiga de decisão
4. **Revisão > planejamento** — a revisão semanal é o ritual mais importante
5. **Seus dados são seus** — tudo vive na sua máquina, em arquivos que você controla

### Dicas

- **Use o `inbox.md` sem dó** — jogue tudo lá entre sessões. O briefing matinal organiza.
- **Seja honesto nos perfis** — o Claude só ajuda com o que sabe. Quanto mais contexto, melhor o coaching.
- **Não pule revisões semanais** — são o coração do sistema. 10 minutos é melhor que zero.
- **Personalize as áreas** — os padrões são ponto de partida. Adicione, renomeie ou remova.
- **Commit sempre** — `git commit` depois de cada sessão para manter o histórico da sua evolução.
- **Input por voz funciona muito bem** — ferramentas como Wispr Flow ou ditado do macOS permitem falar com o Claude naturalmente.

</details>

---

## Credits

Built by [Victor Marcondes](https://www.linkedin.com/in/victormarcondes/). Inspired by the need for a personal system that actually sticks — powered by AI that remembers context across sessions.

## License

MIT — use it, fork it, make it yours.
