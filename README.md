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
├── day-10/         # Day 10: (Upcoming)
├── day-11/         # Day 11: (Upcoming)
├── LICENSE         # MIT License
└── README.md       # This file
```

---

## 📅 Day-wise Summary

| Day | Topic | Dataset | Key Deliverables |
|-----|-------|---------|------------------|
| **Day 8** | Data Filtering, Sorting & Observations | `Day8_Ecommerce_Sales_Dataset.csv` (100 transactions) | EDA, Category/Region/Payment insights, Recommendations |
| **Day 9** | Data Merging, Concatenation & Feature Engineering | Orders (120) + Customers (30) + Products (20) | Merged dataset, `Order_Type`, `Total_Price`, Temporal features |
| **Day 10** | *Coming Soon* | — | — |
| **Day 11** | *Coming Soon* | — | — |

---

## 🚀 Quick Start

Each day folder is self-contained:

```bash
cd day-8
jupyter notebook "IDRA DAY 8.ipynb"
# or
cd day-9
jupyter notebook "IDRA DAY 9.ipynb"
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

---

## 👤 Author

**Patel Harshilkumar Rajubhai**  
Information Technology & Data Analytics  
[GitHub](https://github.com/Harshil2992005)