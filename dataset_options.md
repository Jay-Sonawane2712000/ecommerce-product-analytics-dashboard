# Dataset Options

Project goal: choose a public dataset that works well for product analytics, funnel analysis, cohort retention analysis, and dashboarding.

I did not download anything yet. This is only a recommendation memo.

## Option 1: GA4 BigQuery sample ecommerce dataset

Source:
- Google Analytics developer docs: https://developers.google.com/analytics/bigquery/web-ecommerce-demo-dataset

What it contains:
- Obfuscated Google Analytics 4 ecommerce event data from the Google Merchandise Store.
- Three months of event export data from `2020-11-01` to `2021-01-31`.
- Event-level web analytics data suitable for product and ecommerce behavior analysis.

Supports funnel analysis?
- Yes.
- This is one of the strongest options for funnel work because it is event-level analytics data and closely matches real product analytics workflows.

Supports cohort retention analysis?
- Yes, with some care.
- The dataset includes user-level event data, so you can build acquisition cohorts and return behavior cohorts.

Why it is a good fit:
- Very realistic for modern product analytics.
- Great if you want practice with event schemas, session/user analysis, and dashboards that look like real analytics work.

Why it is a weaker fit:
- It requires working in BigQuery and a Google Cloud project.
- Google notes the data is obfuscated and has some internal consistency limits.
- For a first Codex project, the setup overhead may distract from the analytics itself.

## Option 2: eCommerce events history in electronics store

Source:
- Kaggle: https://www.kaggle.com/datasets/mkechinov/ecommerce-events-history-in-electronics-store

What it contains:
- Event-level ecommerce behavior from an electronics store over five months, from `2019-10` to `2020-02`.
- About `900K` user events.
- Includes fields like `event_time`, `event_type`, `product_id`, `category_id`, `category_code`, `brand`, `price`, `user_id`, and `user_session`.
- Event types include `view`, `cart`, `remove_from_cart`, and `purchase`.

Supports funnel analysis?
- Yes.
- This dataset is directly suited to funnels like `view -> cart -> purchase`, plus cart abandonment analysis.

Supports cohort retention analysis?
- Yes.
- Because it includes `user_id` and timestamps across multiple months, you can create first-visit or first-purchase cohorts and measure repeat activity over time.

Why it is a good fit:
- Strong match for all four goals: product analytics, funnel analysis, cohort retention, and dashboarding.
- Much more approachable than the very large multi-category REES46 dataset.
- CSV-style event data is beginner-friendly for Python, pandas, SQL, and dashboard tools.
- The size is large enough to feel real, but still manageable for a first serious project.

Why it is a weaker fit:
- It is still an ecommerce dataset, so it represents product analytics through a retail lens rather than a SaaS app lens.
- Some cleaning and aggregation work will still be needed before dashboarding.

## Option 3: UCI Online Retail

Source:
- UCI Machine Learning Repository: https://archive.ics.uci.edu/dataset/352/online+retail

What it contains:
- Transactional online retail data for a UK-based non-store retailer.
- Covers transactions between `2010-12-01` and `2011-12-09`.
- Around `541,909` rows.
- Includes invoice, product, quantity, timestamp, price, customer ID, and country.

Supports funnel analysis?
- No, not well.
- It contains completed transactions, not detailed pre-purchase events like product views or add-to-cart behavior.

Supports cohort retention analysis?
- Yes.
- It is good for purchase cohort analysis, repeat purchase rates, customer segmentation, and revenue retention style analysis.

Why it is a good fit:
- Very beginner-friendly to load and explore.
- Clean and widely used for retail analytics learning.
- Good for dashboards around sales, repeat purchasing, customer cohorts, and geographic patterns.

Why it is a weaker fit:
- Weak choice for funnel analysis because the upstream behavior is missing.
- If your goal is a product analytics dashboard with behavioral funnels, this dataset only covers the bottom of the journey.

## Recommendation

Best choice for a beginner-friendly first Codex project:

**`eCommerce events history in electronics store`**

Why this is the best first choice:
- It supports both funnel analysis and cohort retention analysis without requiring cloud setup.
- It is event-level, which makes it much more aligned with product analytics than a transactions-only dataset.
- It is much smaller and more manageable than the giant multi-category ecommerce event datasets.
- It should work well with a simple local workflow using Python, pandas, notebooks, and a dashboard later.

Suggested positioning for this project:
- Treat it as an ecommerce product analytics case study.
- Build metrics around sessions, product views, cart adds, purchases, conversion rates, repeat users, and monthly retention cohorts.

## Short ranking

1. `eCommerce events history in electronics store` - best overall fit and best beginner balance
2. `GA4 BigQuery sample ecommerce dataset` - strongest real analytics flavor, but heavier setup
3. `UCI Online Retail` - easiest to start, but not strong for funnels

## Notes from sources

- Google’s GA4 sample dataset page says the public BigQuery dataset contains three months of obfuscated ecommerce event export data and requires access to a Google Cloud project with BigQuery enabled.
- The Kaggle electronics events dataset page states it includes five months of ecommerce events and the event types `view`, `cart`, `remove_from_cart`, and `purchase`.
- The UCI Online Retail page describes the dataset as transaction data for a UK-based online retailer with `541,909` instances and variables such as invoice date, quantity, unit price, customer ID, and country.
