# Data Dictionary — Retail Revenue Intelligence

## Dataset Summary

- Domain: Retail Transactions  
- Granularity: One row per transaction  
- Rows (raw): 12,575  
- Rows (cleaned): 11,971  
- Columns: 11  
- Time Range: Jan 2022 – Dec 2024  
- Source: Kaggle (dirty dataset for cleaning)  
- Primary Use: Revenue analysis, KPI computation, Tableau dashboards  

---

## Column Definitions

| Column Name        | Data Type   | Description |
|-------------------|------------|------------|
| Transaction ID     | String     | Unique identifier for each transaction (e.g., TXN_XXXXX) |
| Customer ID        | String     | Unique identifier for each customer (e.g., CUST_XX) |
| Category           | String     | Product category (e.g., Food, Beverages, Furniture) |
| Item               | String     | Specific product identifier within a category |
| Price Per Unit     | Float      | Price of a single unit of the item |
| Quantity           | Integer    | Number of units purchased in the transaction |
| Total Spent        | Float      | Total transaction value |
| Payment Method     | String     | Mode of payment (Cash, Credit Card, Digital Wallet) |
| Location           | String     | Sales channel (Online or In-store) |
| Transaction Date   | Date       | Date of transaction (DD/MM/YY format) |
| Discount Applied   | Boolean    | Indicates whether a discount was applied (TRUE/FALSE) |

---

## Derived Columns

| Column Name        | Logic |
|-------------------|------|
| Revenue Check      | Price Per Unit × Quantity (used to validate Total Spent) |
| Year               | Extracted from Transaction Date |
| Month              | Extracted from Transaction Date |
| Day                | Extracted from Transaction Date |
| Average Order Value (AOV) | Total Revenue / Total Transactions |
| Total Revenue      | Sum of Total Spent |
| Total Units Sold   | Sum of Quantity |
| Discount Flag Cleaned | Missing values filled as FALSE |

---

## Data Quality Notes

- Missing Values
  - Item, Price Per Unit, Quantity, and Total Spent contain nulls
  - Discount Applied has missing values → treated as FALSE  

- Inconsistent Rows
  - Some rows have Quantity but missing Price or Total
  - Some rows have Total but missing Price/Quantity → cannot verify calculation

- Data Integrity Issues
  - Total Spent not always equal to Price × Quantity
  - Requires recalculation or validation during cleaning

- Categorical Noise
  - Category naming consistent but requires validation for grouping
  - Payment methods standardized into 3 types

- Date Format
  - Stored as string initially
  - Converted to datetime during preprocessing

- Outliers
  - High quantities and totals may skew revenue metrics
  - Needs statistical handling during EDA

- Small Customer Base
  - Only ~25 unique customers → limits segmentation depth  

- No Cost Data
  - Only revenue available → no profit analysis possible  

---

## Assumptions

- Missing discounts = no discount applied  
- Transactions with critical missing numeric values may be removed or imputed  
- Revenue is the primary metric (no margin/profit dimension available)  
