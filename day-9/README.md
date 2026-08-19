# 📊 E-Commerce Data Integration & Feature Engineering

**Student Name:** Patel Harshilkumar Rajubhai  
**Project Track:** Day 9 Data Merging, Concatenation & Feature Engineering  
**Datasets:** `Day9_Orders.csv` (120 Transactions), `Day9_Customers.csv` (30 Customers), `Day9_Products.csv` (20 Products)

---

## 📌 Executive Summary

This project demonstrates end-to-end data integration techniques using pandas, combining three relational datasets (Orders, Customers, Products) into a unified analytics-ready dataset. The workflow covers data loading, exploration, concatenation, multi-table joins, derived feature creation, and temporal feature extraction — core skills for retail analytics and data engineering pipelines.

---

## 🔍 Dataset Architecture & Parameters

The project integrates **three normalized CSV files** into a single denormalized analytical dataset:

| Dataset | Records | Key Attributes |
|---------|---------|----------------|
| **Orders** | 120 transactions | Order_ID, Order_Date, Customer_ID, Product_ID, Quantity, Payment_Method, Order_Status |
| **Customers** | 30 customers | Customer_ID, Customer_Name, City, Region (North/South/East/West), Membership_Type (Premium/Regular/New) |
| **Products** | 20 products | Product_ID, Product_Name, Category (Electronics/Clothing/Home & Kitchen/Books/Sports), Unit_Price, Brand |

**Final Merged Dataset:** 120 rows × 18+ columns (including engineered features)

---

## 🛠️ Technical Workflow & Operations

### 1. Data Loading & Exploration
- Loaded three independent CSV files using `pd.read_csv()`
- Inspected schema, dtypes, and sample records for each table
- Verified referential integrity (Customer_ID, Product_ID present across tables)

### 2. Concatenation Demo (`pd.concat`)
- Demonstrated vertical stacking: combined first 5 and last 5 order records
- Used `ignore_index=True` to reset index after concatenation
- Extracted specific columns for focused analysis

### 3. Multi-Table Joins (`pd.merge`)
- **Left Join 1:** Orders ← Customers on `Customer_ID` (preserves all orders, enriches with customer demographics)
- **Left Join 2:** Result ← Products on `Product_ID` (adds product catalog details)
- **Join Type:** Left joins ensure no order records are lost even if customer/product lookup fails

### 4. Feature Engineering
| Feature | Logic | Business Purpose |
|---------|-------|------------------|
| **Order_Type** | `Quantity >= 3 → 'Bulk'`, else `'Single/Small'` | Segment orders for fulfillment planning & pricing strategy |
| **Total_Price** | `Quantity × Unit_Price` | Base revenue metric before discounts/membership adjustments |

### 5. Temporal Feature Extraction
Converted `Order_Date` to datetime and derived:
- `Month` (numeric), `Month_Name` (string)
- `Day` (day of month)
- `Day_of_Week` (Monday–Sunday)
- Enables time-series analysis, seasonality detection, weekday/weekend patterns

### 6. Export
- Saved unified dataset as `Ecommerce_Dataset.csv` for downstream modeling/reporting

---

## 📈 Key Technical Insights

1. **Data Normalization → Denormalization:** Transformed 3NF relational structure into analysis-ready wide format
2. **Join Strategy:** Left joins from fact table (Orders) to dimension tables (Customers, Products) is standard star-schema pattern
3. **Feature Engineering at Scale:** Vectorized operations (`apply` with lambda, `dt` accessor) avoid row-wise loops
4. **Concatenation vs Merge:** `concat` for same-schema stacking; `merge` for relational enrichment
5. **Datetime Parsing:** Critical for any temporal aggregation — `pd.to_datetime()` + `dt` accessor unlocks 10+ time features

---

## 🎯 Applications & Next Steps

1. **Revenue Analysis:** Aggregate `Total_Price` by Category, Region, Membership_Type
2. **Cohort Analysis:** Track `New` vs `Premium` customer lifetime value
3. **Demand Forecasting:** Use `Day_of_Week`, `Month` seasonality + `Order_Type` for inventory planning
4. **A/B Testing Framework:** `Order_Type` (Bulk vs Small) as treatment indicator for promotion experiments
5. **ML Feature Store:** Export engineered dataset as baseline for churn prediction, recommendation, or sales forecasting models

---

## 👤 Author Information

* **Student Name:** Patel Harshilkumar Rajubhai  
* **Topic:** Relational Data Integration, Feature Engineering & Temporal Analysis