# 📚 IDRA Assignment Week 2-4

**Student:** Patel Harshilkumar Rajubhai  
**Track:** Data Analytics & E-Commerce Business Intelligence  
**Duration:** Week 2-4 (Days 8-11+)

---

## 📁 Project Structure

```
IDRA-Assignment-WEEK2-4/
├── day-8/          # Day 8: Data Filtering, Sorting & Observations
├── day-9/          # Day 9: Data Merging, Concatenation & Feature Engineering
├── day-10/         # Day 10: Flight Operations Data Analysis
├── LICENSE         # MIT License
└── README.md       # This file
```

---

## 📅 Day-wise Summary

| Day | Topic | Dataset | Key Deliverables |
|-----|-------|---------|------------------|
| **Day 8** | Data Filtering, Sorting & Observations | `Day8_Ecommerce_Sales_Dataset.csv` (100 transactions) | EDA, Category/Region/Payment insights, Recommendations |
| **Day 9** | Data Merging, Concatenation & Feature Engineering | Orders (120) + Customers (30) + Products (20) | Merged dataset, `Order_Type`, `Total_Price`, Temporal features |
| **Day 10** | Flight Operations Data Analysis | `Day10_Flight_Operations_Dataset.csv` (180 flights) | Complete Pandas workflow: load, clean, filter, sort, group, aggregate, 8 observations |

---

## 🚀 Quick Start

Each day folder is self-contained:

```bash
cd day-8
jupyter notebook "IDRA DAY 8.ipynb"
# or
cd day-9
jupyter notebook "IDRA DAY 9.ipynb"
# or
cd day-10
jupyter notebook "IDRA DAY 10.ipynb"
```

**Requirements:** `pandas`, `jupyter`

---

## 📊 Day 8 Highlights
- **Top Category:** Sports (₹1.36L revenue)
- **Top Region:** North (38 orders), South (highest AOV: ₹5,245)
- **Payment Leader:** UPI (26 orders), Cards (highest value)
- **Avg Rating:** 4.32/5.0

## 🔧 Day 9 Highlights
- **3-table merge:** Orders ← Customers ← Products (star schema)
- **Features engineered:** `Order_Type` (Bulk/Small), `Total_Price`, `Final_Amount` (with membership discount)
- **Temporal features:** Month, Day, Day_of_Week from Order_Date
- **Export:** `Ecommerce_Dataset.csv` (analysis-ready)

## ✈️ Day 10 Highlights
- **Dataset:** 180 flight records, 17 features (airline, route, aircraft, class, pricing, delays, satisfaction)
- **Cleaning:** Missing delay imputation (median), datetime conversion, per-flight load factor, month extraction
- **Key analyses:** Route-wise delays & satisfaction, weather impact, airline performance, travel class comparison
- **Findings:** Avg ticket ₹6,112 (range ₹1,949–₹27,832); Rain causes highest delays (21.4 min); Delhi-Mumbai route most delayed (33.9 min avg); Load factor 62.2%
- **8 observations** covering pricing, delays, routes, satisfaction, load factor, booking channels, seasonal patterns

---

## 👤 Author

**Patel Harshilkumar Rajubhai**  
Information Technology & Data Analytics  
[GitHub](https://github.com/Harshil2992005)