# Telegram Document Intake

Automated document processing pipeline. Send any file or photo to a Telegram bot and it gets classified by AI, renamed to a standard format, filed to the right Google Drive folder, and logged in a tracking spreadsheet.

## How It Works

1. You send a document, photo, or text message to your Telegram bot
2. n8n receives the message via webhook
3. For files: downloads from Telegram, sends to Claude for classification
4. Claude analyzes the document and returns: category, suggested filename, company name, amounts, dates
5. File gets renamed and moved to the correct Google Drive folder based on classification
6. A row is appended to the tracking spreadsheet with all metadata and a link to the filed document
7. Bot sends you a confirmation message with what it did

## Architecture

The system uses 8 n8n workflows:

| Workflow | Purpose |
|----------|---------|
| **WF-Main** | Entry point. Receives Telegram messages, routes to text or file processing path |
| **Sheet Append** | Sub-workflow tool. Appends classified entries to the tracking spreadsheet |
| **Inbox Status** | Sub-workflow tool. Reports current inbox statistics |
| **Query Sheet** | Sub-workflow tool. Queries the tracking spreadsheet for specific entries |
| **Preview** | Sub-workflow tool. Shows pending entries before execution |
| **Execute** | Sub-workflow tool. Processes and files pending entries |
| **Search** | Sub-workflow tool. Searches across filed documents |
| **Sort Inbox** | Sub-workflow tool. Sorts and prioritizes pending items |

## Tracking Spreadsheet Columns

| Column | Content |
|--------|---------|
| Status | Processing state (Pending, Filed, Error) |
| Source | Where the document came from (Telegram DM, Group, etc.) |
| Timestamp | When received |
| Classification | AI-assigned category |
| Original Filename | What the file was called when sent |
| New Filename | Standardized name after AI classification |
| Company Name | Extracted entity name |
| Extracted JSON | Full AI classification output |
| Amount | Dollar/currency amount if detected |
| Date Extracted | Date found in the document |
| Destination Folder | Where the file was filed in Drive |
| File ID | Google Drive file ID |
| Drive Link | Direct link to the filed document |
| Confidence | AI classification confidence score |
| Subtype | Document subtype (invoice, receipt, contract, etc.) |
| Posted Date | When the entry was posted to the sheet |
| Notes | Any additional context |

## Setup

See [setup.md](setup.md) for step-by-step instructions.
