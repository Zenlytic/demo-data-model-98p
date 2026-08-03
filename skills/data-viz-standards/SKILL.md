---
name: data-viz-standards
description: Standards for every dashboard, chart, diagram, or HTML artifact that presents data, whether interactive or static. ALWAYS use this skill before creating any data visualization, dashboard, report artifact, chart, or interactive diagram, even if the user just says "make a chart", "build a dashboard", "visualize this", "show this data", or "create an HTML report". The skill analyzes the intent of the analysis and the data available, then selects the best chart type, color palette (derived from any base/brand color the user specifies), layout, and storytelling structure. Grounded in established visualization research and practice on perceptual accuracy, color use, and narrative structure.
---

# Data Visualization Standards

This skill defines the standards for any output that visually presents data: dashboards, single charts, interactive HTML artifacts, static SVG/text-based visuals, and reports containing charts.

The core rule: a good visualization is **trustworthy, accessible, and elegant, in that order**. Never sacrifice accuracy for beauty. Every design decision below serves those three in priority order.

## Workflow (always in this order)

### Step 1 - Understand the intent of the analysis

Before choosing anything visual, answer these. If the user's request or the conversation doesn't make them clear, ask rather than guess.

1. **What is the analytical question?** Reduce it to one sentence ("Is revenue growing faster in region A than B?", "Where are users dropping off?").
2. **Which of the 8 analysis intents does it map to?** (comparison, trend/change over time, part-to-whole, distribution, correlation/relationship, ranking, flow/process, geospatial). Most requests are one primary intent plus at most one secondary.
3. **Explanatory or exploratory?**
   - *Explanatory*: the insight is known; the visual's job is to communicate it. Declutter aggressively, highlight one thing, add a takeaway title.
   - *Exploratory*: the user needs to poke at the data themselves. Favor interactivity, filters, tooltips, and denser layouts, but still apply the same encoding and color rules.
4. **Who is the audience and what should they do after seeing it?** Executives scanning for 5 seconds need different density than analysts who will live in the dashboard.

### Step 2 - Profile the data

Determine before picking a chart:
- Variable types: quantitative, ordinal, nominal, temporal, geospatial
- Cardinality: how many categories/series? (This drives most chart and color decisions. >7 series is a forcing function: group, filter, small-multiply, or emphasize+gray.)
- Number of data points and time granularity
- Is there a meaningful zero? Negative values? Wide value ranges (log scale candidate)?
- Missing data / nulls (must be shown honestly, usually in gray, never silently dropped)

### Step 3 - Select the visualization

Read `references/chart-selection.md` and use the intent × data matrix there. Non-negotiable encoding rules (perceptual accuracy ranking):

- Position and length are decoded most accurately; angle, area, and color intensity least. Prefer position/length encodings for the primary quantitative comparison.
- Bar charts start at zero, always. Line charts need not.
- Pie/donut only for part-to-whole with ≤5 slices and one clear dominant slice; otherwise use a bar or stacked bar.
- One chart, one job. If a chart is trying to answer two questions, split it into two charts or small multiples.
- Use preattentive attributes (color, size, position) to make the key point pop within ~500 ms; everything else recedes.
- Interactivity is a supplement, never a substitute: the main insight must be visible without hovering or clicking. Tooltips carry detail, not the message.

### Step 4 - Apply the color standards

Read `references/color-standards.md`. Summary of the system:

- **If the user names a base/brand color**: derive the full palette from it using the rules there (adjusted base for large areas, shades for subcategories, 2-4 complementary hues chosen at distinct lightness levels, warm/cool grays matched to the base's temperature, sequential gradient built from the base with lightness range ≥60 points and a hue shift if the base can't go dark while staying saturated).
- **If no base color is given**: use the skill's default palette defined in that file.
- Gray is the most important color: all context, axes, gridlines, de-emphasized series, "Other", and missing data are gray. Saturated color is reserved for the data that carries the message.
- Fewer colors beats more colors. Before adding a hue, run the fewer-colors checklist in the reference (same color + direct labels, shades not hues, emphasize one + gray the rest, merge categories, change chart type, small multiples).
- Every palette must pass: distinguishable in grayscale (different lightnesses), colorblind-safe (never red vs green as the only signal), ≥3:1 contrast against background for essential marks.
- Semantic colors are fixed: negative/down = red family, positive/up = green or blue family (prefer blue+red or orange+blue when colorblindness matters), missing = gray. Never invert these.

### Step 5 - Storytelling and layout

Read `references/storytelling.md`. Summary:

- Every explanatory visual gets a **takeaway title** (the finding, e.g. "Churn concentrated in accounts onboarded without training"), not a label title ("Churn by cohort"). Subtitle carries the metric definition and period.
- Dashboards follow the narrative Z: top-left answers "how are we doing" (KPIs with comparison vs target/prior period), middle explains "why" (trends, breakdowns), bottom/right carries "what specifically" (detail tables, drill-down). One screen, one story; don't make users scroll to get the main answer.
- Annotate directly on the chart (direct labels, reference lines, callouts) instead of relying on legends when there are ≤6 series.
- Declutter by default: no chart borders, no heavy gridlines, no redundant axis titles, no 3D, no decorative gradients or shadows on data marks. Every pixel of ink must earn its place (data-ink ratio).
- End with the "so what": explanatory artifacts include a one-line insight or recommended action near the chart, not just the picture.

### Step 6 - Build

- For HTML artifacts, also follow the frontend-design skill for typography and page chrome; this skill governs the data layer (marks, encodings, palette, annotations).
- Prefer a single self-contained HTML file. Charts via SVG or a bundled lib already available in the environment; no external font/CDN dependencies that can break offline sharing.
- Number formatting: humanize (1.2M not 1200000), consistent decimals, thousands separators, explicit units and currency, and state the timezone/period for time data.
- Static/plain-text outputs (markdown tables, ASCII summaries) follow the same intent logic: lead with the answer, order rows by the analytical question (ranked, not alphabetical, unless lookup is the intent), and bold or mark the key row instead of coloring everything.

### Step 7 - Self-check before delivering

Run this checklist; fix anything that fails:
1. Can a first-time viewer state the main takeaway in 5 seconds?
2. Does the chart type match the intent from Step 1 (not just "what the data allows")?
3. Would the chart still work printed in grayscale?
4. Is anything colored that doesn't need to be?
5. Do all bars start at zero; are axes and scales honest (no truncation tricks, dual axes only with strong justification and clear labeling)?
6. Are units, period, and data source stated?
7. If interactive: does it degrade gracefully, i.e. is the insight visible with zero interaction?