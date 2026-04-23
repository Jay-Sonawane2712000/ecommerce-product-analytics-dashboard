# Dashboard Plan

## Project Title

Product Analytics Dashboard with Cohort Analysis

## Main Business Story

This dashboard tells the story of how users move through the ecommerce journey and where the biggest opportunities for improvement exist.

The core business questions are:

- How much traffic reaches each stage of the funnel
- Where the biggest conversion drop-offs happen
- How funnel performance changes over time
- Which categories and brands convert best
- Whether users return after their first observed month

The overall narrative for the dashboard should be:

1. Start with headline KPIs to show the size of user activity and conversion performance.
2. Show the funnel to highlight where users drop off.
3. Show monthly trends to explain whether performance is improving or weakening over time.
4. Show category and brand comparisons to identify what is driving stronger conversion.
5. Finish with cohort retention to show whether users come back after their first month.

This makes the project feel like a real product analytics case study instead of a collection of disconnected charts.

## Recommended Dashboard Structure

For a beginner-friendly but professional Tableau Public project, use either:

- one dashboard with clearly separated sections, or
- two dashboard pages

Recommended option:

### Dashboard 1: Funnel and Performance Overview

Purpose:
- Tell the main conversion story
- Show where users drop off
- Highlight which product groups perform best

### Dashboard 2: Cohort Retention

Purpose:
- Show whether users return after their first observed month
- Add a retention lens to the funnel story

This two-page setup is easier to design cleanly and avoids overcrowding.

## KPI Cards To Include

Use `kpi_summary.csv` for KPI cards.

Recommended KPI cards:

- Total Events
- Unique Users
- Unique Sessions
- Total Views
- Total Carts
- Total Purchases
- View-to-Cart Rate
- Cart-to-Purchase Rate
- View-to-Purchase Rate

Optional small text footer:
- Date Range Start
- Date Range End

Why these matter:
- They give the viewer quick context on scale, engagement, and conversion efficiency before looking at detailed charts.

## Recommended Charts And Data Sources

### 1. KPI Card Row

Use file:
- `kpi_summary.csv`

Chart type:
- KPI cards or BANs (big number cards)

Best fields to show:
- `metric_name`
- `metric_value`

Display suggestion:
- Format rate metrics as percentages
- Format counts with commas

### 2. Overall Funnel Chart

Use file:
- `funnel_summary.csv`

Chart type:
- Horizontal bar chart or funnel-style bar chart

Best fields to show:
- `funnel_stage`
- `event_count`
- `conversion_from_previous_stage`
- `conversion_from_view`

Purpose:
- Show the size of each stage and the main drop-off pattern from `view` to `cart` to `purchase`

### 3. Monthly Funnel Trend

Use file:
- `monthly_trends.csv`

Chart type:
- Multi-line chart

Best fields to show:
- `event_month`
- `total_views`
- `total_carts`
- `total_purchases`

Optional secondary chart:
- Line chart for `view_to_purchase_conversion_rate`

Purpose:
- Show whether funnel activity and conversion are stable, improving, or declining over time

### 4. Monthly Conversion Rate Chart

Use file:
- `monthly_trends.csv`

Chart type:
- Line chart or grouped bar chart

Best fields to show:
- `event_month`
- `view_to_cart_conversion_rate`
- `cart_to_purchase_conversion_rate`
- `view_to_purchase_conversion_rate`

Purpose:
- Separate volume trends from conversion efficiency trends

### 5. Top Category Performance

Use file:
- `category_performance.csv`

Chart type:
- Sorted horizontal bar chart

Best fields to show:
- `category_name`
- `view_to_purchase_conversion_rate`
- `total_views`
- `total_purchases`

Purpose:
- Highlight which categories convert best after filtering to meaningful traffic volume

Recommended setup:
- Sort descending by `view_to_purchase_conversion_rate`
- Use tooltip to include `total_views`, `total_carts`, and `total_purchases`

### 6. Top Brand Performance

Use file:
- `brand_performance.csv`

Chart type:
- Sorted horizontal bar chart

Best fields to show:
- `brand_name`
- `view_to_purchase_conversion_rate`
- `total_views`
- `total_purchases`

Purpose:
- Show which brands are strongest at turning views into purchases

Recommended setup:
- Sort descending by `view_to_purchase_conversion_rate`
- Use tooltip to include `total_views`, `total_carts`, and `total_purchases`

### 7. Cohort Retention Heatmap

Use file:
- `cohort_heatmap.csv`

Chart type:
- Heatmap

Best fields to show:
- `cohort_month`
- `months_since_first_event`
- `retention_rate`

Purpose:
- Show how retention declines across later months for each user cohort

Recommended setup:
- Put `cohort_month` on rows
- Put `months_since_first_event` on columns
- Color by `retention_rate`
- Show retention percentage in labels or tooltips

## Recommended Dashboard Pages Or Sections

## Page 1: Executive Overview

Suggested sections:

### Section A: KPI Header

Contents:
- KPI cards from `kpi_summary.csv`

Goal:
- Give a fast summary of traffic and conversion

### Section B: Funnel Section

Contents:
- Overall funnel chart from `funnel_summary.csv`

Goal:
- Show where the largest drop-off happens

### Section C: Monthly Trend Section

Contents:
- Monthly volume trend from `monthly_trends.csv`
- Monthly conversion rate trend from `monthly_trends.csv`

Goal:
- Show whether performance changes over time

### Section D: Product Performance Section

Contents:
- Top categories chart from `category_performance.csv`
- Top brands chart from `brand_performance.csv`

Goal:
- Show what parts of the catalog convert best

## Page 2: Retention Analysis

Suggested sections:

### Section A: Retention Summary Text

Contents:
- A short annotation box summarizing average month 1 retention and the largest cohort

Goal:
- Help the viewer interpret the heatmap quickly

### Section B: Cohort Heatmap

Contents:
- Heatmap from `cohort_heatmap.csv`

Goal:
- Show retention patterns clearly across cohorts and elapsed months

## Most Important Insights To Highlight

Based on the outputs already created, the dashboard should call attention to these findings:

- The funnel is heavily top-of-funnel weighted: views are much higher than carts and purchases.
- The biggest drop-off is between `view` and `cart`, which suggests a major opportunity to improve product page engagement and add-to-cart behavior.
- The cart-to-purchase rate is relatively strong compared with the earlier stage, which suggests that users who reach cart are much more likely to convert.
- Monthly conversion performance improved in `2021-02`, which may suggest better intent, seasonality, or a shift in traffic quality.
- Some categories and brands convert much better than others, so product mix matters.
- Retention falls quickly after the first month, which suggests the business is stronger at acquisition than repeat engagement.

You should surface these as short annotation callouts directly in Tableau, not just leave them for the caption.

## Suggested Beginner-Friendly Tableau Layout

## Option: Two-Dashboard Portfolio Layout

### Dashboard 1 Layout

Top row:
- 5 to 6 KPI cards

Middle left:
- Funnel chart

Middle right:
- Monthly conversion trend

Bottom left:
- Top categories bar chart

Bottom right:
- Top brands bar chart

Optional footer:
- Date range and short project note

### Dashboard 2 Layout

Top row:
- Title and one short explanatory text box

Main area:
- Large cohort heatmap

Optional side panel:
- One or two text callouts summarizing average month 1 retention and the largest cohort month

## Visual Design Suggestions

Keep the Tableau design simple and professional:

- Use one primary blue palette for funnel and retention visuals
- Use one accent color for category and brand comparison charts
- Keep backgrounds light and uncluttered
- Use consistent number formatting across all charts
- Show percentages with one decimal place or two decimals where needed
- Use short chart titles with plain language

Examples:
- `Overall Funnel`
- `Monthly Conversion Trend`
- `Top Categories by Purchase Conversion`
- `Top Brands by Purchase Conversion`
- `Cohort Retention Heatmap`

## Filters And Interactivity

For a first version, keep filters minimal.

Recommended filters:
- `event_month` if needed on trend pages
- Possibly `category_name` or `brand_name` only if the layout stays clean

Recommended interactive behavior:
- Hover tooltips on category and brand charts
- Click-to-highlight actions between category and brand visuals only if simple

Avoid:
- Too many global filters
- Overly complex dashboard actions
- Small text or crowded legends

## Final Deliverable Goal

The finished Tableau Public project should feel like a clear analytics story:

- strong top-level KPIs
- a clear funnel drop-off narrative
- easy-to-read time trends
- product performance comparisons
- a strong cohort retention ending

That combination will make the project look portfolio-ready, business-oriented, and practical for entry-level analytics roles.
