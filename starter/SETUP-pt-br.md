# Personal OS — Guia de Instalação

Não precisa saber programar. Só siga os passos.

---

## O que você vai ter

Um sistema operacional pessoal rodando no seu terminal — briefings diários, revisões semanais, sessões de coaching, registro de decisões e acompanhamento de áreas da vida. Tudo com IA, tudo salvo em arquivos de texto que são seus.

## Passo 1: Instale o Claude Code

Claude Code é uma ferramenta de linha de comando da Anthropic. Você precisa dela pra rodar o sistema.

**No Mac:**
```bash
brew install claude-code
```

**Em qualquer sistema com npm:**
```bash
npm install -g @anthropic-ai/claude-code
```

Se você não tem npm, instale o [Node.js](https://nodejs.org/) primeiro (baixe a versão LTS e instale — o npm já vem junto).

Depois de instalar, rode `claude` uma vez no terminal pra autenticar com sua conta da Anthropic.

Documentação completa: https://docs.anthropic.com/en/docs/claude-code

## Passo 2: Crie sua pasta

Abra o terminal e rode:

```bash
mkdir personal-os
cd personal-os
```

Isso cria uma pasta vazia onde o sistema vai morar.

## Passo 3: Adicione o arquivo CLAUDE.md

Baixe o arquivo `CLAUDE.md` desta pasta e coloque dentro da sua pasta `personal-os`.

Ou copie e cole: abra o arquivo `CLAUDE.md` neste diretório, copie o conteúdo inteiro e salve como `CLAUDE.md` dentro da pasta `personal-os`.

Sua pasta deve ficar assim:
```
personal-os/
└── CLAUDE.md
```

## Passo 4: Deixe o Claude montar seu sistema

Abra o terminal, navegue até a pasta e inicie o Claude:

```bash
cd personal-os
claude
```

Então digite este prompt:

> **"Set up my personal OS. Read the CLAUDE.md file and create the full system — all directories, templates, and slash commands. Then walk me through filling in my profile."**

O Claude vai:
1. Ler as instruções do CLAUDE.md
2. Criar todas as pastas e arquivos de template
3. Criar os slash commands (briefing matinal, revisão semanal, coaching, decisões)
4. Fazer perguntas pra preencher seu perfil, valores, contexto familiar e metas

Isso leva uns 5-10 minutos. É só responder as perguntas do Claude.

## Passo 5: Comece a usar

Quando o setup terminar, você pode começar a usar. Abra o Claude na sua pasta a qualquer momento:

```bash
cd personal-os
claude
```

### Comandos diários

| O que digitar | O que faz |
|--------------|-----------|
| `/morning` | Briefing matinal — processa inbox, define prioridades, dá uma cutucada de coaching |
| `/weekly` | Revisão semanal — avalia áreas da vida, celebra conquistas, planeja próxima semana |
| `/decide` | Pensar numa decisão difícil com frameworks estruturados |
| `/coaching` | Sessão de coaching aprofundada sobre qualquer problema |

### Linguagem natural

Você também pode simplesmente conversar:

- "Preciso pensar se aceito essa proposta de emprego"
- "Atualiza minha área de saúde — comecei a correr essa semana"
- "O que tenho pra fazer essa semana?"
- "Adiciona minha amiga Maria no tracker de pessoas"

### A inbox

Entre sessões, jogue pensamentos, tarefas e ideias no arquivo `inbox.md`. Seu briefing matinal vai processar tudo.

Você pode editar o `inbox.md` com qualquer editor de texto, ou simplesmente dizer pro Claude:

> "Adiciona na inbox: ligar pro dentista, revisar orçamento do Q2, ver aquele podcast que a Maria recomendou"

## Passo 6: Salve seu progresso (opcional mas recomendado)

Se quiser manter um histórico da sua evolução, inicialize o git:

```bash
cd personal-os
git init
git add -A
git commit -m "Setup inicial"
```

Depois de cada sessão, salve suas mudanças:

```bash
git add -A
git commit -m "Briefing diario 2025-03-11"
```

Ou simplesmente peça pro Claude: "faz commit das minhas mudanças".

## Dicas

- **O briefing matinal é o ritual mais importante.** Tente fazer todo dia útil.
- **Não pule revisões semanais.** 10 minutos é melhor que zero.
- **Seja honesto nos perfis.** Quanto mais contexto o Claude tem, melhor o coaching.
- **Use o inbox.md sem dó.** Jogue tudo lá — o briefing matinal organiza.
- **Input por voz funciona muito bem.** Ferramentas como Wispr Flow ou ditado do macOS permitem falar com o Claude naturalmente.

## Avançado: Conecte ferramentas externas

Quando estiver confortável com o básico, você pode conectar ferramentas externas pra turbinar o sistema:

- **Gmail** — triagem de email com IA usando `/gmail`
- **Google Calendar** — agenda do dia no seu briefing matinal
- **Google Meet** — processamento automático de transcrições com `/meetsync`
- **Trello / Todoist / Google Tasks** — sync de tarefas

Isso requer configuração de MCP (Model Context Protocol). A opção mais fácil é o [Rube](https://rube.app/), que dá acesso a Gmail, Google Calendar, Google Docs, Trello e mais de 500 outros apps.

**Como instalar o Rube no Claude Code:**

1. Rode isso no terminal:
   ```bash
   claude mcp add rube --transport http https://rube.app/mcp
   ```
2. No Claude Code, digite `/mcp` pra abrir o gerenciamento de servidores MCP
3. Selecione **Rube** na lista e aperte enter
4. Selecione **Authenticate** e aperte enter
5. Uma janela do navegador vai abrir — complete a autenticação lá
6. Volte pro Claude Code e pronto

Depois de autenticar o Rube, você pode conectar apps individuais (Gmail, Google Calendar, etc.) direto no Claude Code — é só pedir pro Claude te ajudar a conectar.

Para configuração manual sem o Rube, veja a [documentação de MCP do Claude Code](https://docs.anthropic.com/en/docs/claude-code/mcp).

Cada slash command que usa MCP (`/gmail`, `/meetsync`) inclui instruções de setup — abra o arquivo do comando em `.claude/commands/` pra ver o que é necessário.

---

## Resolução de problemas

**"Command not found: claude"**
- Verifique se o Claude Code está instalado. Rode `npm install -g @anthropic-ai/claude-code` e tente de novo.

**"O Claude não parece conhecer o sistema"**
- Verifique se o arquivo `CLAUDE.md` está na mesma pasta onde você está rodando o `claude`. Ele lê esse arquivo automaticamente.

**"Baguncei alguma coisa"**
- Se configurou o git, pode desfazer: `git checkout .`
- Se não, diga pro Claude: "Reseta meu sistema — recria todos os templates a partir do CLAUDE.md"

**"Quero começar do zero"**
- Delete a pasta e refaça a partir do Passo 2. O arquivo CLAUDE.md é o blueprint — todo o resto pode ser regenerado.
