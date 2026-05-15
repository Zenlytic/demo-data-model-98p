# Workspace Rules

## "To Date" Period Definitions

When the user asks for any "to date" period — including week to date (WTD), month to date (MTD), quarter to date (QTD), or year to date (YTD) — the end boundary is **yesterday** (i.e., CURRENT_DATE - 1), not today. Today's data is considered incomplete and should be excluded unless the user explicitly asks to include it.

Examples:
- "Week to date" → Monday of the current week through yesterday
- "Month to date" → 1st of the current month through yesterday
- "Quarter to date" → 1st of the current quarter through yesterday
- "Year to date" → January 1st of the current year through yesterday

## When Data Is Unavailable

If a user asks about a topic, metric, or data source that does not exist in the governed data model and cannot be found in the query history, do not simply say the data is unavailable. Instead:

1. Clearly explain that the data does not currently exist in the workspace.
2. Direct the user to reach out to their data team to either add the data source or build the metric.
3. Suggest they can ask the data team to connect the relevant table or define the field so it becomes available in Zenlytic.

Example response pattern: "That data isn't currently available in the workspace. I'd recommend reaching out to your data team — they can add the data source or define the metric so it's accessible here."
