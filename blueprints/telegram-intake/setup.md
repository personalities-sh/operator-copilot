# Setup: Telegram Document Intake

## What You Need Before Starting

- An n8n instance (self-hosted on Railway, Docker, or n8n Cloud)
- A Telegram account
- A Google account with Drive and Sheets access
- An Anthropic API key

## Step 1: Create the Telegram Bot

1. Open Telegram and message @BotFather
2. Send `/newbot`
3. Choose a name and username for your bot
4. Save the bot token BotFather gives you
5. Send `/setprivacy` to @BotFather, select your bot, and choose "Disable" (so the bot can see messages in groups)

## Step 2: Set Up Google Sheets

Create a new Google Sheet with these column headers in row 1:

```
Status | Source | Timestamp | Classification | Original Filename | New Filename | Company Name | Extracted JSON | Amount | Date Extracted | Destination Folder | File ID | Drive Link | Confidence | Subtype | Posted Date | Notes
```

Save the spreadsheet ID from the URL (the long string between `/d/` and `/edit`).

## Step 3: Set Up Google Drive Folders

Create a folder structure in Google Drive for your document categories. Example:

```
Document Intake/
├── 01 Contracts/
├── 02 Invoices/
├── 03 Receipts/
├── 04 Reports/
├── 05 Correspondence/
└── 09 Inbox/          <- unclassified items land here
```

Save the root folder ID from the Drive URL.

## Step 4: Import n8n Workflows

The `workflows/` directory contains 8 JSON files. Import them into your n8n instance:

1. Open your n8n instance
2. Go to Workflows > Import from File
3. Import each JSON file in this order:
   - `sheet-append.json` (sub-workflow)
   - `inbox-status.json` (sub-workflow)
   - `query-sheet.json` (sub-workflow)
   - `preview.json` (sub-workflow)
   - `execute.json` (sub-workflow)
   - `search.json` (sub-workflow)
   - `sort-inbox.json` (sub-workflow)
   - `wf-main.json` (main workflow - import last)

## Step 5: Configure Credentials in n8n

For each workflow, you need to set up credentials:

1. **Telegram**: Settings > Credentials > Add New > Telegram API. Paste your bot token.
2. **Google Drive**: Settings > Credentials > Add New > Google Drive OAuth2. Follow the OAuth flow.
3. **Google Sheets**: Settings > Credentials > Add New > Google Sheets OAuth2. Follow the OAuth flow.
4. **Anthropic**: Settings > Credentials > Add New > Anthropic API. Paste your API key.

Then open each workflow and connect the credentials to the appropriate nodes.

## Step 6: Update Workflow Variables

In the main workflow (`wf-main.json`), update these values:

- Google Sheet ID (in Sheet Append and Query Sheet nodes)
- Google Drive folder IDs (in the file routing logic)
- Telegram bot token (should auto-connect from credentials)
- Any whitelisted Telegram user IDs for access control

## Step 7: Activate and Test

1. Activate the main workflow in n8n
2. Send a test document to your Telegram bot
3. Check that:
   - The bot acknowledges receipt
   - A new row appears in your tracking spreadsheet
   - The file appears in the correct Google Drive folder
   - The bot sends a confirmation with the classification

## Troubleshooting

**Bot doesn't respond:** Check that the main workflow is active and the Telegram trigger node has the correct bot token.

**Files not appearing in Drive:** Verify Google Drive credentials have write access to the destination folders.

**Empty spreadsheet rows:** Check the Anthropic API key is valid and the classification prompt is returning structured JSON.

**"Unauthorized" errors:** Verify all credentials are connected in each workflow's nodes, not just created in settings.
