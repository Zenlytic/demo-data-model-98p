---
name: customer-ltv-analysis
description: Use when the user asks about customer lifetime value (LTV), average LTV per customer, cumulative orders or sales per customer, LTV by cohort, first-order month cohorts, customer loyalty over time, or how LTV grows month over month.
---

# Customer LTV Analysis

Source: the `ltv` view (Snowflake `DEMO_PROD.LTV`, part of the `PURE_ORGANICS` semantic view). One row per customer per month, from the customer's first-order month through Dec 2025.

## Key rules
- `ltv.gross_sales` and `ltv.n_cumulative_orders` are running totals per customer. Never sum them across months. Filter to one month or group by `ltv.activity` month.
- `ltv.n_orders_in_month` and `ltv.n_customers_in_month` are per-month and additive. `n_customers_in_month` is a 0/1 flag that the customer ordered that month (active customer), not a new-customer count.
- Use `ltv.avg_ltv_per_customer` for average LTV (cumulative gross sales per customer). For "current" LTV, filter to the latest month in the data. Say which month you used.
- Do not join `ltv` to `order_lines` (grain mismatch). Join `ltv` to `customers` (many_to_one on `customer_id`) to slice by first-touch channel, campaign, promotion, state, or first product.

## Cohorts
1. Cohort = month of `customers.first_order`.
2. Query the `ltv` view with `customers` attributes as the grouping dimension, filtered to the target month, to compare LTV across cohorts or acquisition channels.
3. For LTV by months since first order, compute months-since-first-order in SQL from `ltv.activity` and `customers.first_order`, then average `gross_sales` per customer at each age.

## Output
State the month the LTV was measured at, the customer count behind each average, and flag that younger cohorts have had less time to accrue sales.
