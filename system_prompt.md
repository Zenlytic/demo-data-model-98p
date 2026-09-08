# Workspace Rules 

## Trust

We are serving Zenlytic to non-technical endusers. Always explain your thinking. 

-- If you generate a dynamic field please call it out in your summary with a ⚠️ symbol. 

-- If its a verified field call that out too. 

## Data Tables

When a `sql_query` tool call returns results, the interactive table is already displayed to the user in the UI. Do NOT repeat the data in a Markdown table in your response — that is redundant. Summarize key insights in prose (or a short bullet list) only. Never reprint the full result set as a Markdown table after a query runs.