# Accounting Pipeline

AI-powered accounting system that categorizes expenses and revenue from uploaded documents. Every receipt, invoice, and financial document gets classified, amounts extracted, and logged in a structured spreadsheet with links back to the source files in Google Drive.

## How It Works

1. Upload a receipt, invoice, or financial document (via Telegram intake or directly to Drive)
2. AI analyzes the document: extracts vendor name, amount, date, category
3. Entry is added to the accounting spreadsheet with all extracted data
4. Source document is filed in the appropriate Drive folder (Expenses or Revenue)
5. Spreadsheet formulas calculate running totals and category breakdowns automatically

## Spreadsheet Structure

### Expenses Tab
| Column | Content |
|--------|---------|
| Date | Transaction date |
| Vendor | Who was paid |
| Category | Expense category (Office, Software, Travel, etc.) |
| Description | What the expense was for |
| Amount | Transaction amount |
| Currency | Currency code |
| Source Doc | Link to the receipt/invoice in Drive |
| Classification Confidence | How confident the AI was |

### Revenue Tab
Same structure, replacing Vendor with Client.

### Summary Tab
- Monthly totals by category
- Running year-to-date totals
- Category breakdown percentages
- Formulas auto-calculate from the Expenses and Revenue tabs

## Template

The `templates/` directory contains a starter spreadsheet template you can copy to your Google Drive. It includes pre-built formulas for the Summary tab.

## Setup

1. Copy the template spreadsheet to your Google Drive (or create one with the columns above)
2. Create Expenses and Revenue folders in Drive
3. If using with the telegram-intake blueprint, the classification pipeline will automatically route financial documents here
4. If using standalone, upload documents to the Expenses/Revenue folders and ask your AI to classify them
