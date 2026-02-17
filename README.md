# Operator Copilot

AI partner for non-developer business operators who think in systems. Built for people who understand architecture and strategy but work through their AI to implement.

## What This Is

A portable persona configuration that changes how your AI agent communicates, prioritizes, and works. Not a prompt dump you paste into a chat box. A structured behavioral package that persists across every conversation.

## What It Does

**Communication:** Direct, anti-sycophantic, no filler. Says "that won't work because X" instead of "that's interesting, but have you considered..." Leads with assessments, not questions. Holds position under challenge unless new information changes the calculus.

**Execution:** Acts instead of reporting. When something is broken and fixable, fixes it. Evaluates no-code tools (n8n, Zapier, Make) before writing custom code. Explains the approach first, gets confirmation, then builds.

**Memory:** Records decisions, corrections, and project state across sessions. After any mistake, writes what it learned. Never repeats the same error.

**Writing:** External-facing text scores low on AI detection. No emdashes, no formulaic structure, no "Here's..." openers.

## Blueprints Included

Complete project systems your AI can build from these specifications:

| Blueprint | Description | Services |
|-----------|------------|----------|
| [Telegram Document Intake](blueprints/telegram-intake/) | Bot that receives documents via Telegram, classifies with AI, files to Google Drive, logs in a spreadsheet | n8n, Telegram, Google Drive, Sheets, Anthropic |
| [AI Task Management](blueprints/task-management/) | Telegram-triggered task management with AI prioritization and Google Sheets tracking | n8n, Telegram, Google Sheets |
| [Accounting Pipeline](blueprints/accounting-pipeline/) | Expense and revenue categorization from uploaded receipts and invoices | Google Sheets, Google Drive, Anthropic |

## Install

Paste this into Claude Code, Cursor, Windsurf, or any AI agent:

```
Install the Operator Copilot persona from github.com/adbcjay/operator-copilot — clone the repo, read the setup instructions, ask me for my personal details, replace all template variables, copy the files to the right config locations, and walk me through connecting any integrations it needs.
```

For manual setup, see [SETUP.md](SETUP.md).

## Compatible With

- Claude Code
- Cursor
- Windsurf
- Codex CLI
- GitHub Copilot

## Format

Built on the [personalities.sh](https://site-self-rho.vercel.app) persona format specification. Browse more personas at the catalog.

## License

MIT
