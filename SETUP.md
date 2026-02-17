# Setup: Operator Copilot

## Prerequisites

- An AI coding agent that reads markdown config files (Claude Code, Cursor, Windsurf, Codex CLI, or Copilot)
- A GitHub account (for cloning the repo)

## Installation

The fastest way to install: paste this into your AI agent:

```
Install the Operator Copilot persona from github.com/adbcjay/operator-copilot — clone the repo, read the setup instructions, ask me for my personal details, replace all template variables, copy the files to the right config locations, and walk me through connecting any integrations it needs.
```

Your AI will handle the rest. It will:
1. Clone this repository
2. Ask you for your name, company, role, timezone, and industry
3. Replace all `{{VARIABLE}}` placeholders with your answers
4. Copy PERSONA.md to your agent's config location
5. Walk you through connecting any MCP servers you want

## Manual Installation

If you prefer to set things up yourself:

### 1. Clone the repo

```bash
git clone https://github.com/adbcjay/operator-copilot.git
cd operator-copilot
```

### 2. Edit PERSONA.md

Open `PERSONA.md` and replace these placeholders with your information:

| Placeholder | Replace With |
|-------------|-------------|
| `{{YOUR_NAME}}` | Your full name |
| `{{YOUR_COMPANY}}` | Your company or organization |
| `{{YOUR_ROLE}}` | Your role (e.g., COO, founder, head of ops) |
| `{{YOUR_TIMEZONE}}` | Your timezone (e.g., Asia/Dubai) |
| `{{YOUR_INDUSTRY}}` | Your industry |

### 3. Copy to your agent's config

**Claude Code:**
```bash
cp PERSONA.md ~/.claude/CLAUDE.md
```

**Cursor:**
```bash
cp PERSONA.md .cursorrules
```

**Windsurf:**
```bash
cp PERSONA.md .windsurfrules
```

### 4. Optional: Connect MCP Servers

These are not required but unlock additional capabilities:

**Google Drive** (file management):
```bash
npx @anthropic-ai/claude-code mcp add google-drive -- npx @anthropic-ai/gdrive-mcp
```

**n8n** (workflow automation):
```bash
npx @anthropic-ai/claude-code mcp add n8n -- npx @anthropic-ai/n8n-mcp
```

### 5. Test It

Start a conversation with your AI and say:

```
What's your primary directive? How would you describe your communication style?
```

It should respond directly, without hedging or filler. If it opens with "Great question!" the persona didn't load correctly.

## Blueprints

This persona includes three project blueprints in the `blueprints/` directory. These are complete systems your AI can build for you:

| Blueprint | What It Does | Complexity |
|-----------|-------------|-----------|
| **Telegram Document Intake** | Bot that receives files, classifies them with AI, files to Google Drive | Complex |
| **AI Task Management** | Telegram-triggered task tracking with AI prioritization | Medium |
| **Accounting Pipeline** | Expense/revenue categorization from uploaded receipts | Medium |

To set up a blueprint, tell your AI:

```
Read the telegram-intake blueprint in the operator-copilot repo and set it up for me.
```

Each blueprint has its own `setup.md` with requirements and step-by-step instructions.
