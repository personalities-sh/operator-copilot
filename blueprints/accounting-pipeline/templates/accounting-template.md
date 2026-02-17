# Accounting Spreadsheet Template

Create a Google Sheet with three tabs:

## Tab 1: Expenses

Row 1 headers:
```
Date | Vendor | Category | Description | Amount | Currency | Source Doc | Confidence
```

Categories to use:
- Office & Supplies
- Software & Subscriptions
- Travel & Transportation
- Professional Services
- Marketing & Events
- Rent & Utilities
- Salaries & Wages
- Government & Licensing
- Insurance
- Miscellaneous

## Tab 2: Revenue

Row 1 headers:
```
Date | Client | Category | Description | Amount | Currency | Source Doc | Confidence
```

Categories to use:
- Licensing Fees
- Advisory Fees
- Consulting
- Lab Services
- Reimbursements
- Other Revenue

## Tab 3: Summary

### Monthly Totals (row 1-15)
- Row 1: Month headers (Jan through Dec + YTD)
- Row 2: Total Expenses (SUMIFS from Expenses tab by month)
- Row 3: Total Revenue (SUMIFS from Revenue tab by month)
- Row 4: Net (Revenue - Expenses)
- Rows 6-15: Expense breakdown by category

### Example formulas
Total expenses for January:
```
=SUMIFS(Expenses!E:E, Expenses!A:A, ">="&DATE(YEAR(TODAY()),1,1), Expenses!A:A, "<"&DATE(YEAR(TODAY()),2,1))
```

Revenue for January:
```
=SUMIFS(Revenue!E:E, Revenue!A:A, ">="&DATE(YEAR(TODAY()),1,1), Revenue!A:A, "<"&DATE(YEAR(TODAY()),2,1))
```

Your AI can create this spreadsheet for you using the xlsx skill or Google Sheets MCP.
