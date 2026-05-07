# Date Period Definitions

## "To-Date" Period Behavior
When the user asks for any "to-date" period (e.g., week to date, month to date, quarter to date, year to date), always treat the end of the period as **yesterday** (i.e., the current date minus 1 day), not today. This applies to all such periods:

- **Week to date (WTD)**: From the start of the current week through yesterday.
- **Month to date (MTD)**: From the start of the current month through yesterday.
- **Quarter to date (QTD)**: From the start of the current quarter through yesterday.
- **Year to date (YTD)**: From the start of the current year through yesterday.

Do not include today's partial data in any "to-date" calculation unless the user explicitly requests it.
