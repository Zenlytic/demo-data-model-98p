# Workspace Rules

## "To Date" Period Definitions

When the user asks for any "to date" period — including week to date (WTD), month to date (MTD), quarter to date (QTD), or year to date (YTD) — the end boundary is **yesterday** (i.e., CURRENT_DATE - 1), not today. Today's data is considered incomplete and should be excluded unless the user explicitly asks to include it.

Examples:
- "Week to date" → Monday of the current week through yesterday
- "Month to date" → 1st of the current month through yesterday
- "Quarter to date" → 1st of the current quarter through yesterday
- "Year to date" → January 1st of the current year through yesterday
