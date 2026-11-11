# Workspace Rules 

## Trust

We are serving Zenlytic to non-technical endusers. Always explain your thinking. 

-- If you generate a dynamic field please call it out in your summary with a ⚠️ symbol. 

-- If its a verified field call that out too. 

## Data Tables

When a `sql_query` tool call returns results, the interactive table is already displayed to the user in the UI. Do NOT repeat the data in a Markdown table in your response — that is redundant. Summarize key insights in prose (or a short bullet list) only. Never reprint the full result set as a Markdown table after a query runs.

## Year-over-Year Margin / "Biggest Drop" Questions

When a user asks which products (or other segments) had the biggest YoY drop, decline, or change in margin, answer the question first. Then, especially if the changes are small or margins are broadly flat, say plainly that the ranking is not meaningful and offer these follow-up questions:

1. Where is margin structurally low? Compare margin across products, since differences between products are usually larger than changes over time. This is a pricing or cost question.
2. Where did profit dollars change? Rank products by change in gross profit (`order_lines.GROSS_PROFIT`), since dollars can move even when the margin percentage does not.
3. Is there a trend inside the year? Show monthly margin by product to catch a late-year slide that a year-to-date comparison can hide.
4. Is the discount spend worth it? Compare margin and repeat rate for promoted orders against orders with no promotion.

Offer these as a short list and ask which the user wants to run next. Do not run them unprompted.

## Pure Organics Data Model Map

The model mirrors the Snowflake semantic view `DEMO.DEMO_PROD.PURE_ORGANICS`. Pick the view by question:

- Revenue, margin, discounts, orders, repurchase, subscription vs. one-time, new vs. repeat: `order_lines` (join to `products` and `customers`).
- Customer attributes and first-touch attribution: `customers`.
- Customer lifetime value (cumulative, per customer-month): `ltv` (load the `customer-ltv-analysis` skill).
- Paid spend, CAC, ROAS, PROAS: `marketing_spend`. It does not join to other views, so combine with order data after aggregating each.
- Site traffic, sessions, funnel conversion: `events`.
- `customers_orimi`, `order_facts` and `product_facts` are duplicates or derived roll-ups; do not use them unless explicitly asked.

