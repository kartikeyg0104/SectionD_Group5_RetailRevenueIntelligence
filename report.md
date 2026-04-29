# Data Visualization & Analytics — Final Project Report

## Retail Revenue Intelligence: Unlocking Sales Performance Through Data-Driven Insights

---
### 1. Cover Page

| Field | Details |
|---|---|
| **Project Title** | Retail Revenue Intelligence |
| **Sector** | Retail / Consumer Goods |
| **Team ID** | Section D — Group 5 |
| **Team Members & Roles** | Divy Kumar Jain — Team Lead | Data Cleaning, EDA & Statistical Analysis|
                           | Tanisha Dhiman — Tableau Dashboards & Data Sourcing |
                           | Kartikey Gupta — Tableau Dashboards |
                           | Disha Khanka — Presentation (PPT & Viva) |
                           | Yash Raj — Report Writing |
| **Faculty Mentor** | Satyaki Das |
| **Institute** | Newton School of Technology |
| **GitHub Repository URL** | [https://github.com/kartikeyg0104/SectionD_Group5_RetailRevenueIntelligence](https://github.com/kartikeyg0104/SectionD_Group5_RetailRevenueIntelligence) |
| **Tableau Public Dashboard — Executive Overview** | [Dashboard 1](https://public.tableau.com/app/profile/tanisha.dhiman.dhiman/viz/DVAPROJECT2/Dashboard1?publish=yes) |
| **Tableau Public Dashboard — Customer Analysis** | [Dashboard 2](https://public.tableau.com/app/profile/tanisha.dhiman.dhiman/viz/DVAPROJECT2/Dashboard2?publish=yes) |
| **Tableau Public Dashboard — Sales & Category Performance** | [Dashboard 3](https://public.tableau.com/app/profile/tanisha.dhiman.dhiman/viz/DVAPROJECT2/Dashboard3?publish=yes) |
| **Submission Date** | 29 April 2026 |

---

### 2. Executive Summary

**Problem:** A multi-category retail business needed to understand the true drivers of its ₹15.5 lakh+ revenue across 11,971 transactions spanning January 2022 to December 2024. Without clear visibility into which product categories, customer segments, sales channels, payment methods, and promotional strategies were performing — and which were underperforming — the business lacked the evidence base to optimise pricing, inventory, and marketing decisions.

**Approach:** Transaction-level point-of-sale data (12,575 records, 11 fields) was sourced and processed through a rigorous five-stage Python pipeline: extraction, cleaning, exploratory analysis, statistical testing, and final load preparation. The cleaned dataset (11,971 records, zero missing values) was then loaded into Tableau to build three interactive dashboards — an Executive Overview, a Customer Analysis view, and a Sales & Category Performance view — enabling stakeholders to self-serve insights at any time.

**Key Insights:**

1. **Butchers is the highest-revenue category** (₹2.08 lakh, average order value ₹139.12), while Milk Products significantly trails the field (₹1.19 lakh average, lowest among all eight categories). An ANOVA test confirmed that category-level spending differences are statistically significant (p < 0.001).
2. **Discounts do not meaningfully lift basket size.** A Welch's t-test (p = 0.49, Cohen's d = 0.01) revealed no statistically significant difference in average transaction value between discounted and non-discounted purchases, suggesting the current discount programme is eroding margin without increasing revenue.
3. **Online and In-Store channels contribute almost equally** (₹7.91 lakh vs ₹7.61 lakh), with Online holding a slight edge in transaction count (6,068 vs 5,903). ANOVA confirms the difference is not statistically significant (p = 0.37).
4. **Quantity sold is the strongest predictor of transaction value** (Pearson r = 0.71, p ≈ 0), followed by price per unit (r = 0.63), indicating that upselling additional units has more revenue impact than price increases alone.

**Key Recommendations:**

1. **Redesign the discount strategy** — shift from blanket discounts to targeted, category-specific promotions (e.g., bundling low-performing Milk Products with high-performing Butchers items) to protect margins while stimulating demand where it is most needed.
2. **Invest in quantity-driven upselling tactics** across both channels, such as multi-buy offers, since unit quantity is the single largest driver of transaction value.
3. **Prioritise Butchers and Electric Household Essentials categories** for inventory depth and marketing spend, as they generate the highest revenue and average order values.

---



### 3. Sector & Business Context

**Sector Overview:**
The retail and consumer-goods sector is one of the largest contributors to global GDP. It encompasses brick-and-mortar stores, e-commerce platforms, and omni-channel operations that sell a diverse mix of products — from perishable food items and beverages to furniture and electronics. The dataset in this project covers eight distinct product categories (Beverages, Butchers, Computers & Electric Accessories, Electric Household Essentials, Food, Furniture, Milk Products, and Patisserie), reflecting a typical multi-department retail store or supermarket environment.

**Current Industry Challenges:**

- **Margin compression:** Increasing input costs and competitive price pressure force retailers to optimise every lever — pricing, promotions, and assortment.
- **Channel fragmentation:** Consumers now shop seamlessly across online and in-store channels, demanding a unified view of performance.
- **Discount dependency:** Retailers frequently rely on blanket discounts to drive footfall, but without data evidence these promotions often erode margins without proportionally increasing volume.
- **Customer retention:** With 25 unique customers in this dataset, understanding per-customer lifetime value and purchasing behaviour is critical for targeted engagement.

**Target Decision-Maker:**
This project serves **retail business managers, category heads, and operations directors** who need to make daily decisions about inventory allocation, pricing strategy, promotional spend, and channel investment.

**Why This Problem Was Chosen:**
Retail generates enormous volumes of transactional data, yet many operators still rely on intuition rather than evidence when setting prices, choosing which categories to promote, or allocating marketing budgets between online and in-store channels. By applying a structured analytics pipeline (Python + Tableau) to real retail transaction data, this project demonstrates how data-driven decision-making can replace guesswork — directly improving revenue, margin, and customer satisfaction.

**Business Value:**
Solving this problem enables the retailer to (a) identify and double down on high-performing categories, (b) eliminate wasteful discount spending, (c) balance investment across channels based on evidence rather than assumption, and (d) understand customer-level value to inform loyalty and retention programmes.

---

### 4. Problem Statement & Objectives

**Formal Problem Definition:**
The retail business lacks a systematic, data-driven understanding of the factors that drive — or inhibit — revenue performance across its product categories, customer base, sales channels, payment methods, and promotional strategies. As a result, strategic decisions regarding pricing, inventory allocation, discount deployment, and channel investment are made on the basis of intuition rather than evidence, leading to sub-optimal resource utilisation and missed revenue opportunities.

**Project Scope:**

*In Scope:*
- Analysis of retail store sales transactions from January 2022 to December 2024.
- Data extraction, cleaning, and transformation using Python (pandas, NumPy, SciPy).
- Exploratory Data Analysis (EDA) covering trends, distributions, comparisons, and correlations.
- Statistical hypothesis testing: t-tests, one-way ANOVA, Pearson correlation, confidence intervals.
- KPI computation: Total Revenue, Average Order Value (AOV), Transaction Count, Quantity Sold, Revenue by Category/Channel/Payment Method/Discount Status.
- Interactive Tableau dashboards for executive and operational decision-making.
- Actionable business recommendations with estimated impact.

*Out of Scope:*
- Predictive or machine-learning-based forecasting models.
- Real-time data ingestion or streaming analytics.
- Customer demographic or geographic segmentation beyond the fields available in the dataset.
- Cost-of-goods-sold (COGS) or profit-margin analysis (not available in source data).

**Success Criteria:**

1. A fully cleaned, analysis-ready dataset with zero missing values and validated data integrity (price × quantity = total_spent for every row).
2. At least 8 statistically grounded insights supported by hypothesis tests at the 95% confidence level.
3. Three published Tableau dashboards (Executive Overview, Customer Analysis, Sales & Category Performance) with interactive filters for Category, Year, and Location.
4. A minimum of 3 prioritised, actionable business recommendations, each linked to a specific insight and an estimated business impact.

---

### 5. Data Description

**Dataset Source:**
The dataset (`retail_store_sales.csv`) is a retail point-of-sale transaction log. It was stored on Google Drive and accessed via Google Colab notebooks. The raw file is located at `data/raw/retail_store_sales.csv` within the project repository.

**Data Structure:**

| Attribute | Value |
|---|---|
| **Raw rows** | 12,575 |
| **Columns** | 11 |
| **Time period** | January 2022 — December 2024 |
| **Unique transactions** | 12,575 (each Transaction ID is unique) |
| **Unique customers** | 25 |
| **Product categories** | 8 |
| **Unique items** | 200 |

**Column-by-Column Explanation:**

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | Transaction ID | String | Unique identifier for each transaction (e.g., TXN_6867343) |
| 2 | Customer ID | String (categorical) | Anonymised customer identifier (CUST_01 to CUST_25) |
| 3 | Category | String (categorical) | Product department — one of 8 categories: Beverages, Butchers, Computers And Electric Accessories, Electric Household Essentials, Food, Furniture, Milk Products, Patisserie |
| 4 | Item | String (categorical) | Specific product code (e.g., Item_10_PAT, Item_17_MILK). 200 unique values |
| 5 | Price Per Unit | Float | Unit price of the item, ranging from ₹5.00 to ₹41.00 (mean ₹23.36, std ₹10.74) |
| 6 | Quantity | Float | Number of units purchased per transaction, ranging from 1 to 10 (mean 5.54) |
| 7 | Total Spent | Float | Transaction value = Price Per Unit × Quantity. Range ₹5.00–₹410.00 (mean ₹129.65, std ₹94.75) |
| 8 | Payment Method | String (categorical) | Payment instrument — Cash, Credit Card, or Digital Wallet |
| 9 | Location | String (categorical) | Sales channel — Online or In-Store |
| 10 | Transaction Date | Date | Date of the transaction (YYYY-MM-DD format) |
| 11 | Discount Applied | Boolean | Whether a promotional discount was applied (True/False). Raw data had ~33.4% missing values in this field |

**Known Data Limitations & Biases:**

1. **Small customer base:** Only 25 unique customers are represented, limiting the generalisability of per-customer behavioural insights.
2. **No cost data:** The dataset contains revenue (Total Spent) but no cost-of-goods-sold, making profit-margin analysis impossible.
3. **Missing discount data:** 33.4% of the raw Discount Applied values were null/missing. During cleaning, these were imputed as `False` (no discount), which may slightly understate the true discount utilisation rate.
4. **Missing numeric fields:** Approximately 4.8% of Price Per Unit, Quantity, and Total Spent values were missing in the raw data. Where two of the three were available, the third was computed; remaining incomplete rows were dropped.
5. **Item-level granularity:** Item codes are anonymised (e.g., Item_6_FOOD), preventing product-name-level analysis.
6. **No demographic data:** Customer age, gender, income, or geography are not available, limiting segmentation depth.

---

### 6. Data Cleaning & ETL Pipeline

All cleaning was executed in Python across `notebooks/01_extraction.ipynb` and `notebooks/02_cleaning.ipynb`. The pipeline followed five stages: Extract → Clean → EDA → Statistical Analysis → Final Load.

**Step 1 — Column Standardisation** *(01_extraction.ipynb):* Headers stripped, lowercased, spaces replaced with underscores.

**Step 2 — Duplicate Removal** *(01_extraction.ipynb):* `drop_duplicates()` applied. All 12,575 Transaction IDs were unique — no duplicates found.

**Step 3 — Data Type Conversion** *(both notebooks):*
- `price_per_unit`, `quantity`, `total_spent` → `float64` via `pd.to_numeric(errors='coerce')`.
- `transaction_date` → `datetime64` via `pd.to_datetime(errors='coerce')`.
- `discount_applied` → cleaned from mixed strings/NaN to boolean; NaN filled with `False`.

**Step 4 — Missing Value Treatment** *(02_cleaning.ipynb):*

| Column | Missing % | Treatment |
|---|---|---|
| item | 9.65% | Filled with `'Unknown'` |
| price_per_unit | 4.84% | Computed as `total_spent / quantity` where possible; else dropped |
| quantity | 4.80% | Computed as `total_spent / price_per_unit` where possible; else dropped |
| total_spent | 4.80% | Computed as `price_per_unit × quantity` where possible; else dropped |
| discount_applied | 33.39% | NaN filled with `False` (assumed no discount) |

**Result after cleaning: 11,971 rows, 0 missing values.**

**Step 5 — Invalid Value Removal:** Rows with non-positive price, quantity, or total were removed.

**Step 6 — Integrity Validation:** Verified `price × quantity = total_spent` for all rows. **0 inconsistent rows.**

**Step 7 — Categorical Standardisation:** `category`, `payment_method`, `location` stripped and Title-Cased.

**Step 8 — Feature Engineering** *(04_statistical_analysis.ipynb, 05_final_load_prep.ipynb):*
- `year`, `month` extracted from `transaction_date`.
- `year_month` derived as period string for monthly KPI aggregation.

**Assumptions:** (1) Missing discounts assumed as no discount. (2) Missing numerics computed deterministically where 2 of 3 fields were available. (3) `'Unknown'` items retained for aggregate analysis only.

**Output:** `data/interim/cleaned.csv` — 11,971 rows × 11 columns.

---

### 7. KPI & Metric Framework

All KPIs were computed in `notebooks/05_final_load_prep.ipynb` and exported to `data/processed/` for Tableau ingestion.

| # | KPI | Formula / Logic | Actual Value | Why It Matters | Mapped Objective |
|---|---|---|---|---|---|
| 1 | **Total Revenue** | `SUM(total_spent)` | ₹15,52,071 | Top-line health indicator; answers "how much did we earn?" | Understand overall performance |
| 2 | **Total Transactions** | `COUNT(transaction_id)` | 11,971 | Volume indicator; reveals demand intensity | Measure transaction volume |
| 3 | **Average Order Value (AOV)** | `MEAN(total_spent)` | ₹129.65 | Revenue efficiency per transaction; critical for pricing decisions | Optimise pricing strategy |
| 4 | **Total Quantity Sold** | `SUM(quantity)` | 66,268 units | Throughput measure; helps inventory planning | Inform inventory allocation |
| 5 | **Unique Customers** | `NUNIQUE(customer_id)` | 25 | Customer base breadth | Assess customer reach |
| 6 | **Revenue by Category** | `GROUPBY(category).SUM(total_spent)` | Butchers highest (₹2,08,118); Milk Products lowest (₹1,80,036) | Identifies winning vs underperforming departments | Category investment decisions |
| 7 | **Revenue by Location (Channel)** | `GROUPBY(location).SUM(total_spent)` | Online ₹7,91,401; In-Store ₹7,60,670 | Quantifies omni-channel balance | Channel investment strategy |
| 8 | **Revenue by Payment Method** | `GROUPBY(payment_method).SUM(total_spent)` | Cash ₹5,37,710; Credit Card ₹5,07,082; Digital Wallet ₹5,07,279 | Reveals customer payment preferences | Payment infrastructure decisions |
| 9 | **Avg Spend by Discount Status** | `GROUPBY(discount_applied).MEAN(total_spent)` | Discount: ₹130.49; No Discount: ₹129.23 | Tests whether discounts actually lift basket size | Discount programme ROI |
| 10 | **Monthly Revenue Trend** | `GROUPBY(year_month).SUM(total_spent)` | Ranges from ₹33,690 to ₹52,912 per month | Tracks seasonality and growth trajectory | Seasonal planning |
| 11 | **Customer Total Spend** | `GROUPBY(customer_id).SUM(total_spent)` | Ranges from ₹52,824 (CUST_18) to ₹71,831 (CUST_12) | Identifies high-value vs low-value customers | Customer retention strategy |
| 12 | **Customer Transaction Count** | `GROUPBY(customer_id).COUNT(transaction_id)` | Ranges from 424 to 527 per customer | Measures engagement frequency | Loyalty programme design |

---

### 8. Exploratory Data Analysis (EDA)

*Reference: `notebooks/03_eda.ipynb`*

All EDA was performed on the cleaned dataset (11,971 rows). Charts were generated using Matplotlib and Seaborn.

#### 8.1 Trend Analysis — Monthly Revenue

Monthly revenue fluctuates between ₹33,690 and ₹52,912. January 2022 recorded the highest single-month revenue (₹52,912), while several months in mid-2023 dipped below ₹40,000.

**Business Insight:** Revenue does not exhibit a strong upward or downward trend over the three-year period, suggesting the business is in a **steady-state**. ANOVA across months confirms no statistically significant seasonal effect (p = 0.35). This means the retailer cannot rely on natural seasonal spikes and must proactively create demand through targeted campaigns.

#### 8.2 Comparison Analysis — Category Performance

| Category | Total Revenue | Transactions | Avg Order Value |
|---|---|---|---|
| Butchers | ₹2,08,118 | 1,496 | ₹139.12 |
| Electric Household Essentials | ₹2,03,814 | 1,516 | ₹134.44 |
| Beverages | ₹1,97,048 | 1,496 | ₹131.72 |
| Food | ₹1,94,878 | 1,507 | ₹129.27 |
| Computers & Electric Accessories | ₹1,90,693 | 1,477 | ₹129.11 |
| Furniture | ₹1,95,310 | 1,525 | ₹128.07 |
| Patisserie | ₹1,82,173 | 1,441 | ₹126.42 |
| Milk Products | ₹1,80,036 | 1,513 | ₹119.04 |

**Business Insight:** Butchers commands a ₹20 higher AOV than Milk Products. This gap is statistically significant (ANOVA p < 0.001). Milk Products' low AOV is driven by its lower average price-per-unit (₹14.00 vs ₹21.50 for Butchers), not by lower quantities. The retailer should consider **premium-tier Milk Products** or **bundle pricing** to close this gap.

#### 8.3 Comparison Analysis — Payment Methods

| Payment Method | Revenue | Transactions | Avg Spend |
|---|---|---|---|
| Cash | ₹5,37,710 | 4,103 | ₹131.05 |
| Credit Card | ₹5,07,082 | 3,927 | ₹129.13 |
| Digital Wallet | ₹5,07,279 | 3,941 | ₹128.72 |

**Business Insight:** Cash still leads both in transaction volume and average spend, but the difference across payment methods is negligible (ANOVA p = 0.50). This means **no payment method is correlated with higher spending** — the retailer should focus on convenience and speed at checkout rather than incentivising a particular payment channel.

#### 8.4 Comparison Analysis — Location (Channel)

| Channel | Revenue | Transactions |
|---|---|---|
| Online | ₹7,91,401 | 6,068 |
| In-Store | ₹7,60,670 | 5,903 |

**Business Insight:** Online marginally outperforms In-Store by ₹30,731 in revenue and 165 transactions, but the difference is not statistically significant (ANOVA p = 0.37). The business has achieved a **near-perfect omni-channel balance**, which is a strength to preserve rather than disrupt.

#### 8.5 Comparison Analysis — Discount Impact

| Discount Applied | Avg Spent | Total Revenue | Transactions |
|---|---|---|---|
| No | ₹129.23 | ₹10,27,628 | 7,952 |
| Yes | ₹130.49 | ₹5,24,444 | 4,019 |

**Business Insight:** Discounted transactions have an AOV only ₹1.26 higher than non-discounted ones — a difference that is **not statistically significant** (t-test p = 0.49, Cohen's d = 0.01). Yet discounted transactions account for 33.6% of volume but only 33.8% of revenue. This confirms that the current discount strategy is **margin-destructive** — it fails to meaningfully increase basket size while reducing per-unit revenue.

#### 8.6 Distribution Analysis

- **Price Per Unit:** Roughly uniform distribution across 25 distinct price points (₹5 to ₹41), mean ₹23.36, std ₹10.74.
- **Quantity:** Near-uniform from 1 to 10 units, mean 5.54, std 2.86.
- **Total Spent:** Right-skewed, median ₹108.50 vs mean ₹129.65, with a long tail stretching to ₹410.

**Business Insight:** The right skew in Total Spent means a minority of high-value transactions disproportionately contribute to revenue. Identifying and nurturing the customers who generate these high-value baskets is essential for revenue growth.

#### 8.7 Correlation Analysis

| Variable Pair | Pearson r | p-value | Interpretation |
|---|---|---|---|
| Quantity → Total Spent | 0.712 | ≈ 0 | Strong positive |
| Price Per Unit → Total Spent | 0.631 | ≈ 0 | Moderate–strong positive |

**Business Insight:** Quantity has a **stronger influence on transaction value** than price. A customer buying one extra unit increases revenue more than a marginal price hike. This supports a strategic priority on **volume-driving tactics** (multi-buy deals, basket-building promotions) over price increases.

---

### 9. Statistical Analysis

*Reference: `notebooks/04_statistical_analysis.ipynb`*

All statistical tests were conducted using SciPy (`scipy.stats`) at a 95% confidence level (α = 0.05).

#### 9.1 Hypothesis Test — Discount Impact on Spending (Welch's t-test)

- **H₀:** Mean total_spent is equal for discounted and non-discounted transactions.
- **H₁:** Mean total_spent differs between the two groups.
- **Assumptions checked:** Shapiro-Wilk normality test returned p ≈ 0 for both groups (non-normal), but with n > 4,000 per group the Central Limit Theorem applies. Levene's test for equal variances: p = 0.38 (variances are equal), though Welch's t-test was used for robustness.
- **Result:** t-test p = 0.493. **Fail to reject H₀.**
- **Effect size:** Cohen's d = 0.013 (negligible).
- **Business meaning:** Discounts have virtually no impact on basket size. The ₹1.26 difference in average spend is neither statistically nor practically significant. The discount programme should be restructured.

#### 9.2 Hypothesis Test — Category Effect on Spending (One-Way ANOVA)

- **H₀:** Mean total_spent is equal across all 8 product categories.
- **H₁:** At least one category differs.
- **Result:** F-test p = 9.2 × 10⁻⁷. **Reject H₀.**
- **Business meaning:** Category is a statistically significant driver of transaction value. Butchers (₹139.12 AOV) and Electric Household Essentials (₹134.44) lead, while Milk Products (₹119.04) significantly lags. Category-specific strategies are warranted.

#### 9.3 Hypothesis Test — Payment Method Effect (One-Way ANOVA)

- **H₀:** Mean total_spent is equal across Cash, Credit Card, and Digital Wallet.
- **Result:** p = 0.497. **Fail to reject H₀.**
- **Business meaning:** Payment method has no measurable effect on spending. Operational focus should be on checkout speed and reliability, not on steering customers toward a specific method.

#### 9.4 Hypothesis Test — Channel Effect (One-Way ANOVA)

- **H₀:** Mean total_spent is equal for Online and In-Store.
- **Result:** p = 0.368. **Fail to reject H₀.**
- **Business meaning:** Neither channel has a spending advantage. The omni-channel balance is genuine and should be maintained.

#### 9.5 Hypothesis Test — Monthly Seasonality (One-Way ANOVA)

- **H₀:** Mean total_spent is equal across all 12 calendar months.
- **Result:** p = 0.346. **Fail to reject H₀.**
- **Business meaning:** There is no statistically significant seasonal pattern in spending. Revenue fluctuations are driven by factors other than calendar month — likely promotional activity and customer-specific behaviour.

#### 9.6 Correlation Analysis (Pearson)

| Pair | r | p-value | Strength |
|---|---|---|---|
| Price Per Unit vs Total Spent | 0.631 | ≈ 0 | Moderate–strong positive |
| Quantity vs Total Spent | 0.712 | ≈ 0 | Strong positive |

**Business meaning:** Both price and quantity are significant revenue levers, but quantity exerts a stronger pull. A 1-unit increase in quantity yields more incremental revenue than a comparable proportional price increase.

#### 9.7 Confidence Intervals (95%) — Category AOV

| Category | 95% CI Lower | 95% CI Upper |
|---|---|---|
| Beverages | ₹126.72 | ₹136.71 |
| Butchers | ₹134.03 | ₹144.21 |
| Computers & Electric Accessories | ₹124.58 | ₹133.63 |
| Electric Household Essentials | ₹129.62 | ₹139.26 |
| Food | ₹124.69 | ₹133.85 |
| Furniture | ₹123.14 | ₹133.01 |
| Milk Products | ₹114.36 | ₹123.73 |
| Patisserie | ₹121.71 | ₹131.13 |

**Business meaning:** Milk Products' upper confidence bound (₹123.73) is below Butchers' lower bound (₹134.03), confirming the two categories occupy **distinct performance tiers** with no overlap. This reinforces the need for differentiated category strategies.

---

### 10. Tableau Dashboard Design

*Reference: `tableau/dashboard_links.md`*

#### Dashboard Objective

The Tableau dashboards provide a comprehensive, interactive view of overall business performance by analysing sales, customer behaviour, and transaction trends. They help identify key revenue drivers, top-performing categories, customer purchasing patterns, and the impact of discounts on sales. The primary objective is to support business managers in **optimising pricing strategies, improving customer retention, identifying growth opportunities, and ensuring balanced performance** across categories, locations, and time periods.

#### View Structure

| # | Dashboard | Purpose | Tableau Public URL |
|---|---|---|---|
| 1 | **Executive Overview** | High-level KPIs (total revenue, transactions, AOV, discount usage), revenue trends over time, category performance summary | [Dashboard 1](https://public.tableau.com/app/profile/tanisha.dhiman.dhiman/viz/DVAPROJECT2/Dashboard1?publish=yes) |
| 2 | **Customer Analysis** | Customer-level spending, transaction frequency, purchasing patterns, and high-value customer identification | [Dashboard 2](https://public.tableau.com/app/profile/tanisha.dhiman.dhiman/viz/DVAPROJECT2/Dashboard2?publish=yes) |
| 3 | **Sales & Category Performance** | Category-wise revenue breakdown, payment method distribution, location-based performance, and discount impact analysis | [Dashboard 3](https://public.tableau.com/app/profile/tanisha.dhiman.dhiman/viz/DVAPROJECT2/Dashboard3?publish=yes) |

#### Interactive Filters

| # | Filter Name | Filter Type | Purpose |
|---|---|---|---|
| 1 | Category | Dropdown | Filter all visuals by product category |
| 2 | Year | Dropdown | Filter data by year (2022, 2023, 2024) |
| 3 | Location | Dropdown | Filter by Online or In-Store channel |

#### Dashboard View Descriptions

**Dashboard 1 — Executive Overview:**
This view consolidates the most critical KPIs — total revenue, total transactions, average order value, and discount utilisation rate — into a single-screen summary. A time-series line chart displays monthly revenue trends, enabling executives to spot growth or decline at a glance. A horizontal bar chart ranks category performance by total revenue, making it immediately clear which departments are driving the business. All visuals respond to the Category, Year, and Location filters, allowing drill-down without leaving the page.

**Dashboard 2 — Customer Analysis:**
This view shifts the lens from transactions to customers. It visualises per-customer total spend and transaction count, enabling the identification of high-value customers (e.g., CUST_12 with the highest total spend) and low-engagement customers who may need retention interventions. The interactive filters allow managers to examine customer behaviour within specific categories or channels.

**Dashboard 3 — Sales & Category Performance:**
This operational drill-down view presents category-level revenue, payment method distribution (Cash vs Credit Card vs Digital Wallet), and location-based splits (Online vs In-Store). It also visualises the discount impact — comparing average spend for discounted vs non-discounted transactions — reinforcing the statistical finding that discounts are not lifting basket size. This view is designed for category managers and operations teams who need granular, actionable data.

---

### 11. Insights Summary

The following 12 insights are written in **decision language** — each tells the reader what happened, why it happened, and what to do about it.

1. **Butchers is the revenue leader** (₹2.08 lakh, AOV ₹139.12) because it combines relatively high unit prices with strong volume. Stakeholders should **protect and expand this category** through inventory depth, prominent merchandising, and premium product extensions.

2. **Milk Products is the weakest category** (₹1.80 lakh, AOV ₹119.04) because its average unit price is the lowest. The retailer should **introduce premium-tier milk products or cross-sell bundles** with higher-value categories to lift AOV.

3. **Discounts do not increase basket size** (Welch's t-test p = 0.49, Cohen's d = 0.01). The current blanket discount programme is destroying margin without driving incremental revenue. Stakeholders should **replace blanket discounts with targeted, conditional promotions** (e.g., "buy 3 get 1 free" to drive quantity).

4. **Quantity is the strongest revenue lever** (Pearson r = 0.71 vs r = 0.63 for price). Getting customers to buy one more unit generates more revenue than raising prices. The business should **prioritise multi-buy offers and basket-building tactics** over price increases.

5. **Online and In-Store are balanced** (₹7.91L vs ₹7.61L, p = 0.37). This healthy omni-channel equilibrium is a competitive advantage. Stakeholders should **maintain proportional investment** across both channels and avoid cannibalising one in favour of the other.

6. **Payment method does not influence spending** (ANOVA p = 0.50). Cash, Credit Card, and Digital Wallet users spend virtually the same. The focus should be on **checkout convenience and speed** rather than payment-method incentives.

7. **No significant seasonality exists** (ANOVA p = 0.35). Revenue fluctuations are not calendar-driven. The retailer should **create its own demand events** (flash sales, loyalty events) rather than waiting for seasonal peaks.

8. **The customer base is small but relatively even** — 25 customers with total spends ranging from ₹52,824 to ₹71,831. There are no extreme outliers, but the top 5 customers contribute disproportionately. **A tiered loyalty programme** rewarding top spenders would be cost-effective to implement.

9. **Transaction value is right-skewed** (median ₹108.50 vs mean ₹129.65). A minority of high-value transactions pull the average up. Identifying and replicating the conditions of these **high-basket transactions** (e.g., specific categories, multi-unit purchases) can accelerate revenue growth.

10. **Category-level spending differences are statistically significant** (ANOVA p < 0.001). This is not random variation — each category has a genuinely different AOV. **Category-specific pricing and promotion strategies** are therefore justified and should replace one-size-fits-all approaches.

11. **The 95% confidence intervals for Butchers and Milk Products do not overlap** (Butchers: ₹134–₹144; Milk Products: ₹114–₹124). This confirms with high confidence that the performance gap is real, not a sampling artefact. **Intervention in Milk Products is a data-backed priority.**

12. **The data pipeline is production-ready** — 12,575 raw rows were cleaned to 11,971 rows with zero missing values and 100% integrity-validated records. The processed CSVs in `data/processed/` can be **directly consumed by any BI tool** for ongoing monitoring.

---

### 12. Recommendations

Each recommendation is linked to a specific insight, prioritised by estimated impact, and includes a concrete implementation path.

#### Recommendation 1 — Restructure the Discount Programme
- **Linked Insight:** #3 (Discounts do not increase basket size)
- **Priority:** 🔴 High
- **Action:** Eliminate blanket percentage-off discounts. Replace with conditional, quantity-driven promotions: "Buy 3, Get 1 Free" on Milk Products and Patisserie (the two lowest-AOV categories). This simultaneously drives quantity (the strongest revenue lever, r = 0.71) and targets underperforming categories.
- **Estimated Impact:** If conditional promotions lift average quantity by just 0.5 units for the ~4,000 currently discounted transactions, incremental revenue ≈ ₹46,800/year (0.5 × ₹23.36 avg price × 4,019 transactions).
- **Timeline:** 4–6 weeks to design, test, and roll out.

#### Recommendation 2 — Invest in Quantity-Driven Upselling
- **Linked Insight:** #4 (Quantity is the strongest revenue lever)
- **Priority:** 🔴 High
- **Action:** Introduce multi-buy bundles, "frequently bought together" prompts on the online channel, and point-of-sale upselling scripts for in-store staff. Target categories with high unit prices but average quantities (e.g., Butchers, Electric Household Essentials).
- **Estimated Impact:** A 10% increase in average quantity across all transactions (5.54 → 6.09 units) would increase total revenue by approximately ₹1,55,000/year.
- **Timeline:** 2–4 weeks for online implementation; 4–8 weeks for in-store training.

#### Recommendation 3 — Launch a Category-Specific Growth Plan for Milk Products
- **Linked Insight:** #2, #10, #11 (Milk Products is weakest; category differences are significant; CIs do not overlap)
- **Priority:** 🟡 Medium
- **Action:** (a) Introduce a premium Milk Products sub-line (artisanal cheese, organic milk) to lift average price per unit. (b) Bundle Milk Products with Butchers or Beverages at a combo price. (c) Allocate dedicated promotional space (online banners + in-store endcaps) to Milk Products for 8 weeks and measure AOV lift.
- **Estimated Impact:** Closing even half the AOV gap with Butchers (₹10 lift per transaction × 1,513 transactions) would yield ₹15,130 in incremental revenue.
- **Timeline:** 6–10 weeks including sourcing, pricing, and campaign setup.

#### Recommendation 4 — Build a Tiered Customer Loyalty Programme
- **Linked Insight:** #8 (Small but even customer base)
- **Priority:** 🟡 Medium
- **Action:** Create three tiers (Silver, Gold, Platinum) based on cumulative spend thresholds. Offer escalating rewards: early access to new products (Silver), free delivery/priority checkout (Gold), exclusive pricing on premium items (Platinum). With only 25 customers, the programme is low-cost to administer.
- **Estimated Impact:** Industry benchmarks suggest loyalty programmes lift repeat-customer spend by 5–15%. A conservative 5% lift across all customers would add ₹77,600/year.
- **Timeline:** 4–6 weeks for programme design and CRM integration.

#### Recommendation 5 — Create Retailer-Driven Demand Events
- **Linked Insight:** #7 (No natural seasonality)
- **Priority:** 🟢 Low (but strategic)
- **Action:** Since the data shows no organic seasonal peaks, the retailer should manufacture its own demand events — quarterly flash sales, category spotlight weeks, and customer appreciation days. Focus events on underperforming months (historically sub-₹40,000 revenue months).
- **Estimated Impact:** If 3 annual events each lift their respective month's revenue by 15%, incremental revenue ≈ ₹17,500/year.
- **Timeline:** Ongoing; first event within 6 weeks.

---

### 13. Impact Estimation

The recommended actions drive specific, quantifiable outcomes for the business. Stakeholders must act now because the current strategy (blanket discounts and equal category investment) actively erodes margins every month. By executing the recommendations, the business can capture the following impacts:

1. **Revenue Improvement (Upselling):**
   - *Logic:* Quantity is the strongest correlate with Total Spent. The current average quantity is 5.54. Increasing this by just 10% (to 6.09) across 11,971 transactions yields a massive uplift.
   - *Estimated Impact:* ~₹1.55 lakh/year in top-line growth.
   - *Urgency:* Immediate. Every transaction without a bundle offer leaves money on the table.

2. **Margin Protection (Discount Restructuring):**
   - *Logic:* Discounts apply to 33.6% of volume but generate no statistically significant AOV lift. By shifting from percentage-off to conditional "Buy X Get Y" promotions, the retailer stops giving away margin for free and forces volume growth.
   - *Estimated Impact:* ~₹46,800/year in incremental revenue from forced quantity, plus recovered margin from eliminated blanket discounts.
   - *Urgency:* Immediate. Blanket discounts are actively destroying gross margin daily.

3. **Efficiency Gains (Category Optimization):**
   - *Logic:* Milk Products lags Butchers by ₹20 AOV. Introducing premium SKUs or bundling can close this gap.
   - *Estimated Impact:* Closing 50% of the gap (₹10/transaction) for this category yields ~₹15,130/year.
   - *Urgency:* Short-term. The statistical gap is significant and will persist without targeted merchandising.

4. **Customer Lifetime Value (Loyalty Programme):**
   - *Logic:* A small but loyal base of 25 unique customers means retention is critical. Tiered rewards drive frequency and loyalty.
   - *Estimated Impact:* A conservative 5% lift in repeat purchasing yields ~₹77,600/year.
   - *Urgency:* Medium-term. Securing the existing customer base guards against competitor attrition.

---

### 14. Limitations & Assumptions

#### Data Limitations

| # | Limitation | Impact on Analysis | Mitigation Applied |
|---|---|---|---|
| 1 | **Small customer base (n = 25)** | Per-customer behavioural insights have low statistical power; results may not generalise to a larger customer base | Reported customer-level findings as directional; avoided drawing causal conclusions from individual customer data |
| 2 | **No cost/margin data** | Cannot compute profit margins or ROI on promotions | Analysis focused on revenue-side metrics; recommendations flagged as revenue-oriented rather than profit-oriented |
| 3 | **33.4% missing Discount Applied values** | Imputing all NaN as `False` may understate true discount utilisation | Acknowledged in cleaning section; sensitivity analysis recommended as future work |
| 4 | **Anonymised item codes** | Cannot perform product-name-level analysis or tie insights to real SKUs | Analysis conducted at category level (8 categories) rather than item level |
| 5 | **No demographic data** | Cannot segment customers by age, gender, income, or geography | Segmentation limited to behavioural dimensions (spend, frequency, channel, payment) |
| 6 | **3-year static snapshot** | Data does not capture real-time market dynamics or external events (e.g., COVID-19 recovery, inflation) | Findings presented as descriptive of the 2022–2024 period; causal claims avoided |

#### Methodological Assumptions

1. **Central Limit Theorem (CLT):** Although Shapiro-Wilk tests confirmed non-normal distributions for `total_spent`, sample sizes (n > 4,000 per group) are large enough for the CLT to apply, making t-tests and ANOVA valid.
2. **Independence of observations:** Each transaction is treated as an independent observation. In reality, repeat purchases by the same customer may exhibit autocorrelation. This was not modelled.
3. **Homogeneity of variances:** Levene's test (p = 0.38) confirmed equal variances for the discount t-test. For ANOVA tests, homogeneity was assumed but not formally tested for all groupings.
4. **Missing discount imputation:** All missing `discount_applied` values were coded as `False`. If the true distribution of missing values was closer to 50/50, the discount group size would be larger and the t-test result could change — though the negligible effect size (d = 0.01) makes a reversal unlikely.

#### Scope Limitations

- No predictive modelling was performed; all findings are descriptive or inferential.
- External data (competitor pricing, macroeconomic indicators, weather) was not incorporated.
- The Tableau dashboards are published on Tableau Public and are not connected to a live data source — they reflect a static extract of the processed data.

---

### 15. Future Scope

The foundational analytics pipeline established in this project unlocks several avenues for more advanced revenue intelligence:

1. **Predictive Forecasting (Machine Learning):** Transitioning from descriptive to predictive analytics by building a time-series forecasting model (e.g., ARIMA, Prophet) to predict category-level demand for the next 30–90 days, enabling proactive inventory procurement.
2. **Profitability Analysis:** Integrating Cost of Goods Sold (COGS) data to shift the optimization target from *revenue* to *gross margin*. This would reveal whether high-revenue categories like Butchers are also the most profitable.
3. **Market Basket Analysis:** Applying association rule mining (e.g., Apriori algorithm) to identify products frequently bought together. This would provide quantitative evidence for bundle pricing and physical store layout optimization.
4. **Customer Segmentation (RFM Analysis):** Implementing a Recency, Frequency, Monetary (RFM) segmentation model on a larger customer dataset to group customers into distinct cohorts (e.g., "Champions," "At Risk," "Need Attention") for hyper-targeted marketing campaigns.
5. **Real-time Dashboarding:** Upgrading the reporting architecture by connecting Tableau directly to a cloud data warehouse (e.g., Snowflake, BigQuery) with an automated daily ETL pipeline, providing executives with real-time performance tracking instead of static extracts.

---

### 16. Conclusion

This Capstone project successfully transformed raw, incomplete retail transaction logs into a production-grade, interactive Revenue Intelligence system. By applying a rigorous data engineering pipeline to 12,575 records and deploying statistical tests at the 95% confidence level, the analysis replaced retail guesswork with hard, quantifiable evidence.

The analysis revealed that the retailer's core assumption — that blanket discounts drive volume — is mathematically false. Discounts failed to meaningfully lift average order value, acting instead as a silent margin drain. Conversely, the analysis identified that unit quantity, not unit price, is the dominant driver of transaction value. Furthermore, it confirmed that while category performance varies significantly (with Butchers leading and Milk Products lagging), channel performance (Online vs. In-Store) and payment method usage are remarkably balanced.

By bridging the gap between raw data (Python) and executive decision-making (Tableau), this project delivers immediate, actionable value. The five proposed recommendations — ranging from replacing percentage discounts with quantity-driven promotions to executing a category-specific turnaround for Milk Products — provide the management team with a clear, data-backed roadmap to increase average order value, protect margins, and accelerate overall revenue growth.

---

### 17. References

**Data Source:**
1. Retail Store Sales Dataset (`retail_store_sales.csv`). Internal project dataset.

**Software & Analytics Tools:**
2. **Python 3.10+**: Core programming language used for data engineering and statistical analysis.
3. **Google Colaboratory (Colab)**: Cloud-based Jupyter notebook environment used for executing Python code and rendering visualisations.
4. **Tableau Public (2024.1+)**: Business intelligence and data visualisation platform used to build interactive dashboards.

**Python Libraries:**
5. `pandas` (v2.x): Used for data extraction, DataFrame manipulation, cleaning, missing value imputation, and KPI aggregation.
6. `numpy` (v1.x): Used for numerical operations, array manipulation, and statistical formula computation.
7. `scipy.stats` (v1.x): Used for formal hypothesis testing, including `shapiro` (normality), `levene` (variance), `ttest_ind` (Welch's t-test), `f_oneway` (ANOVA), `pearsonr` (correlation), and `t.interval` (confidence intervals).
8. `matplotlib.pyplot` & `seaborn`: Used for generating distribution charts and trend lines during the Exploratory Data Analysis phase.

---

### 18. Appendix

#### A. Repository Directory Structure

```text
SectionD_Group5_RetailRevenueIntelligence/
├── data/
│   ├── raw/                 # Original uncleaned dataset
│   ├── interim/             # Partially processed data (eda_ready.csv, stat_ready.csv)
│   └── processed/           # Final aggregated KPIs for Tableau ingestion
├── notebooks/
│   ├── 01_extraction.ipynb  # Data loading, initial inspection, duplicate removal
│   ├── 02_cleaning.ipynb    # Missing value imputation, datatype fixes, integrity checks
│   ├── 03_eda.ipynb         # Distribution analysis, trend mapping, visualizations
│   ├── 04_statistical_analysis.ipynb  # Hypothesis testing (ANOVA, t-tests, Pearson)
│   └── 05_final_load_prep.ipynb       # KPI aggregation and final CSV exports
├── tableau/
│   └── dashboard_links.md   # Documentation and URLs for Tableau Public dashboards
└── report.md                # Final Project Report (This document)
```

#### B. Instructions for Reproducing the Analysis

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/kartikeyg0104/SectionD_Group5_RetailRevenueIntelligence.git
   cd SectionD_Group5_RetailRevenueIntelligence
   ```
2. **Set up Python Environment:**
   Ensure Python 3.10+ is installed. Install required packages:
   ```bash
   pip install pandas numpy scipy matplotlib seaborn jupyter
   ```
3. **Execute the Pipeline:**
   Open a Jupyter environment and run the notebooks in sequential order (01 through 05). The notebooks are currently configured to read from/write to Google Drive paths (`/content/drive/MyDrive/...`), which must be updated to local relative paths (`./data/...`) if running locally.
4. **Access Dashboards:**
   The Tableau dashboards are hosted publicly and do not require Tableau Desktop to view. Navigate to the URLs provided in Section 1 to interact with the visualizations.

---
[End of Report]
