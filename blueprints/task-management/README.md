# AI Task Management

Task management system operated through Telegram. Send natural language messages to create, update, query, and prioritize tasks. Everything persists in a Google Sheet.

## How It Works

1. Send a message to your Telegram bot: "Add task: review Q1 financials by Friday"
2. n8n processes the message, extracts the task details
3. AI assigns priority based on your project goals and deadlines
4. Task is logged in Google Sheets with status, priority, due date, and timestamps
5. Query your tasks: "What's overdue?" or "Show me all tasks for Project X"

## Task Sheet Columns

| Column | Content |
|--------|---------|
| Task ID | Auto-generated unique identifier |
| Description | What needs to be done |
| Project | Which project this belongs to |
| Priority | AI-assigned (P1/P2/P3) based on goals and deadlines |
| Status | Open, In Progress, Done, Blocked |
| Due Date | When it needs to be completed |
| Created | Timestamp when the task was created |
| Updated | Last modification timestamp |
| Notes | Additional context or updates |

## Commands

Send these as natural language messages to your Telegram bot:

- **Add a task:** "Add task: [description] by [date] for [project]"
- **Update status:** "Mark [task] as done" or "Block [task] because [reason]"
- **Query:** "What's due this week?" or "Show all open tasks"
- **Prioritize:** "Reprioritize based on [new context]"

## Setup

This blueprint builds on top of the telegram-intake infrastructure. If you already have that set up, the same n8n instance and Telegram bot can be extended. See the persona's SETUP.md for general n8n configuration.

To set up:
1. Create a new Google Sheet with the columns listed above
2. Create the task management workflow in n8n (or ask your AI to build it using the architecture described here)
3. Connect to your existing Telegram bot
