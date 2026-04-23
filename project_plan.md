# Project Plan

## Project Title

Product Analytics Dashboard with Cohort Analysis

## Dataset

Dataset selected: `eCommerce events history in electronics store`

Planned use:
- Analyze ecommerce user behavior from event-level data.
- Build a beginner-friendly product analytics case study focused on funnels, cohorts, and dashboard-ready metrics.

## Project Objective

The objective of this project is to use the electronics store event dataset to build a product analytics workflow that answers four main questions:

- How users move through the purchase funnel from `view` to `cart` to `purchase`
- Where the biggest drop-offs happen in the funnel
- How well user cohorts are retained over time
- Which products, brands, and categories contribute most to engagement and conversion

The final project should be easy to explain in a portfolio setting and should result in clean data outputs, analysis notebooks, and dashboard-ready summary tables.

## Expected Dataset Columns

Based on the dataset description, we should expect columns similar to:

- `event_time`
- `event_type`
- `product_id`
- `category_id`
- `category_code`
- `brand`
- `price`
- `user_id`
- `user_session`

Possible event types:
- `view`
- `cart`
- `remove_from_cart`
- `purchase`

Note:
- Exact column names and formatting should be confirmed once the dataset is loaded.
- Some versions of the dataset may include missing values in category or brand fields.

## Columns Needed For Funnel Analysis

The core columns needed for funnel analysis are:

- `event_time`
  - Needed to sort behavior over time and analyze funnel performance by day, week, or month.
- `event_type`
  - Needed to identify funnel stages such as `view`, `cart`, and `purchase`.
- `user_id`
  - Needed to track users moving through the funnel.
- `user_session`
  - Useful for session-based funnel analysis and same-session conversion analysis.
- `product_id`
  - Useful for product-level funnel conversion rates.
- `category_code`
  - Useful for category-level funnel performance.
- `brand`
  - Useful for brand-level conversion comparison.
- `price`
  - Useful for basket value, pricing patterns, and purchase revenue summaries.

Minimum required columns for a basic funnel:
- `event_time`
- `event_type`
- `user_id`

Better practical set for this project:
- `event_time`
- `event_type`
- `user_id`
- `user_session`
- `product_id`
- `category_code`
- `brand`
- `price`

## Columns Needed For Cohort Retention Analysis

The core columns needed for cohort retention analysis are:

- `user_id`
  - Required to identify unique users over time.
- `event_time`
  - Required to assign users to a cohort period and measure return periods.
- `event_type`
  - Useful if we define cohorts based on first `view`, first `cart`, or first `purchase`.
- `purchase`
  - Not a column, but an event value inside `event_type`; important if we decide to use purchase-based cohorts.

Optional supporting columns:
- `user_session`
  - Useful for session frequency analysis but not strictly required for retention tables.
- `category_code`
  - Useful if we later want category-specific cohort cuts.
- `brand`
  - Useful for optional segment-level cohort comparisons.

Recommended cohort definition for this project:
- Primary cohort: month of each user’s first observed event
- Retention measure: whether that user returns in later months with any event activity

Optional secondary cohort:
- Purchase cohort based on the month of the user’s first `purchase`

## Key KPIs To Calculate

### Funnel KPIs

- Total events
- Total unique users
- Total unique sessions
- Total product views
- Total cart events
- Total remove-from-cart events
- Total purchases
- View-to-cart conversion rate
- Cart-to-purchase conversion rate
- View-to-purchase conversion rate
- Session conversion rate
- Purchase frequency by day, week, and month
- Funnel drop-off rate at each step

### Product and Commercial KPIs

- Revenue based on purchase events and `price`
- Average purchase price
- Top categories by views
- Top categories by purchases
- Top brands by views
- Top brands by purchases
- Product-level conversion rate
- Category-level conversion rate
- Brand-level conversion rate

### Cohort KPIs

- Number of users in each acquisition cohort
- Monthly retention rate by cohort
- Repeat activity rate by cohort
- Repeat purchase rate by cohort if purchase-based cohorts are used
- Number of active users by cohort month and return month

## Possible Cleaning Issues

We should expect and check for the following:

- Missing values in `brand`
- Missing values in `category_code`
- Missing or inconsistent `user_session` values
- Duplicate rows
- Event timestamps needing conversion to proper datetime format
- Price stored as string instead of numeric in some exports
- Invalid or zero prices
- Users with only one event type and no further activity
- Multiple events for the same user and product within seconds that may inflate counts
- Purchases without earlier view or cart events in the visible dataset window
- Retention bias caused by the dataset starting mid-user lifecycle

Important analysis note:
- Since the dataset covers a fixed date range, first observed event is not always the true first-ever user event. Cohort results should be described as first observed cohorts within the dataset window.

## Step-By-Step Workflow

### Phase 1: Data Intake and Structure Check

1. Load the raw dataset into the project.
2. Inspect row count, column names, data types, and event type values.
3. Confirm date range and data completeness.
4. Create a short data dictionary for the actual columns.

### Phase 2: Data Cleaning and Preparation

1. Convert `event_time` to datetime format.
2. Standardize text columns where needed.
3. Check and document missing values.
4. Remove exact duplicates if they exist.
5. Cast `price` to numeric.
6. Create derived date fields such as:
   - `event_date`
   - `event_month`
   - `event_week`
7. Validate that `event_type` contains the expected stages.
8. Save a cleaned dataset for analysis use.

### Phase 3: Exploratory Product Analytics

1. Measure total users, sessions, events, and purchases.
2. Summarize event distribution across `view`, `cart`, `remove_from_cart`, and `purchase`.
3. Identify top categories, brands, and products by engagement and purchase activity.
4. Review activity over time to spot seasonality or spikes.

### Phase 4: Funnel Analysis

1. Define the funnel stages:
   - `view`
   - `cart`
   - `purchase`
2. Calculate event counts at each stage.
3. Calculate user-level funnel conversion rates.
4. Calculate session-level funnel conversion rates if session quality is sufficient.
5. Measure drop-off between each stage.
6. Break down funnel performance by:
   - month
   - category
   - brand
7. Create summary tables for dashboard use.

### Phase 5: Cohort Retention Analysis

1. Identify each user’s first observed event month.
2. Assign each user to an acquisition cohort.
3. Measure whether users return in later months.
4. Build a cohort retention matrix.
5. Calculate retention percentages by cohort month.
6. Optionally build a purchase-based cohort table for repeat buyers.
7. Prepare tables for heatmap-style dashboard visuals.

### Phase 6: Dashboard Preparation

1. Create clean aggregated tables for:
   - overall KPI summary
   - funnel metrics
   - time trends
   - category and brand performance
   - cohort retention matrix
2. Ensure output tables are small, readable, and ready for dashboard tools.
3. Save final analysis outputs into the `outputs` folder.

### Phase 7: Documentation

1. Document business questions answered by the project.
2. Document assumptions and limitations.
3. Summarize cleaning steps and KPI definitions.
4. Prepare a short project narrative for the README later.

## Final Outputs We Should Produce

The final project should produce:

- A cleaned analysis-ready dataset
- One or more notebooks that show the analysis process
- A funnel analysis summary table
- A cohort retention matrix
- KPI summary tables for dashboarding
- Category and brand performance tables
- Time-series trend tables
- Visual dashboard assets or screenshots later in the project
- A final README describing the business problem, approach, and key findings

## Scope Notes

This project is intentionally focused on a beginner-friendly but realistic analytics workflow.

In scope:
- Event cleaning
- Funnel metrics
- Cohort retention
- Dashboard-ready outputs

Out of scope for the first version:
- Advanced attribution modeling
- Predictive modeling
- Causal inference
- Real-time pipeline engineering

## Recommended First Analysis Direction

For the first version of the project, the most practical sequence is:

1. Clean the event data
2. Build the main funnel metrics
3. Build monthly user retention cohorts
4. Export summary tables for dashboarding

This keeps the project focused, portfolio-friendly, and achievable without unnecessary complexity.
