# 📚 IDRA Assignment Week 2-4

**Student:** Patel Harshilkumar Rajubhai  
**Track:** Data Analytics & E-Commerce Business Intelligence  
**Duration:** Week 2-4 (Days 8-15)

---

## 📁 Project Structure

```
IDRA-Assignment-WEEK2-4/
├── day-8/          # Day 8: Data Filtering, Sorting & Observations
├── day-9/          # Day 9: Data Merging, Concatenation & Feature Engineering
├── day-10/          # Day 10: Flight Operations Data Analysis
├── day-11/          # Day 11: Company Employee Data Cleaning
├── day-12/          # Day 12: Used Car Data Preprocessing
├── day-13/          # Day 13: Restaurant Branch Performance EDA
├── day-14/          # Day 14: Food Delivery Data Visualization Portfolio
├── day-15/          # Day 15: Executive Hotel Booking EDA Report
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
| **Day 11** | Company Employee Data Cleaning | `Day11_Messy_Company_Employee_Dataset.csv` (157 employees) | Cleaned dataset, missing-value resolution, duplicate removal, dtype fixes, 7 findings |
| **Day 12** | Used Car Data Preprocessing | `Day12_Used_Car_Preprocessing_Dataset.csv` (320 cars) | Leakage-safe pipeline: ordinal + one-hot encoding, IQR outlier capping, StandardScaler, `preprocessed_used_cars.csv` |
| **Day 13** | Restaurant Branch Performance EDA | `Day13_Restaurant_Branch_Performance_Dataset.csv` (350 records) | Complete EDA: summary stats, distribution & correlation analysis, group comparisons, 8 observations |
| **Day 14** | Food Delivery Data Visualization | `Day14_Food_Delivery_Visualization_Dataset.csv` (360 order batches) | 14 Matplotlib/Seaborn charts (line, bar, histogram, scatter, box, violin, heatmap) with interpretations |
| **Day 15** | Executive Hotel Booking EDA Report | `Day15_Executive_Hotel_Booking_EDA_Dataset.csv` (25,180 bookings × 35 columns) | Full-scale EDA: cleaning (22K missing values, duplicates, outliers), datetime fixes, feature engineering, visualizations, 5 insights & 7 recommendations |

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
# or
cd day-11
jupyter notebook "IDRA DAY 11.ipynb"
# or
cd day-12
jupyter notebook "IDRA DAY 12.ipynb"
# or
cd day-13
jupyter notebook "IDRA DAY 13.ipynb"
# or
cd day-14
jupyter notebook "IDRA DAY 14.ipynb"
# or
cd day-15
jupyter notebook "IDRA DAY 15.ipynb"
```

**Requirements:** `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`, `jupyter`

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

## 🧹 Day 11 Highlights
- **Dataset:** 157 employee records, 12 features (identity, org, demographics, compensation, performance, work mode)
- **Cleaning:** 32 missing values resolved (median/mode/ffill), 7 duplicates removed (157→150 rows), strings standardized
- **Imputation:** Median for numeric (Age, Salary, Experience, Performance), Mode for categorical (Department, Gender), ffill/bfill for City/Work Mode
- **Datatype fix:** Joining_Date converted from object to datetime64[ns]
- **7 findings** covering missing data, duplicates, categorical cleanup, imputation strategy, dtype fix, before/after comparison

## 🛠️ Day 12 Highlights
- **Dataset:** 320 used-car records × 15 columns (specs, categories, condition rating, history, resale price)
- **Leakage-safe order:** 80/20 train-test split first; scaler, encoder and outlier bounds fitted on training data only
- **Encoding:** `Condition` ordinal mapping (Poor=0 → Excellent=4), 5 nominal columns one-hot encoded (24 dummies, `drop='first'`)
- **Outliers (IQR, train-only):** Mileage_Km 2, Engine_CC 6, Power_BHP 5 flagged and clipped to fences — all 320 records preserved
- **Deliverable:** `preprocessed_used_cars.csv` — 320 × 33, fully numeric, zero NaNs, scaled features (mean ≈ 0, std ≈ 1)

## 📊 Day 13 Highlights
- **Dataset:** 350 branch-day records × 22 columns (revenue, profit, customers, marketing, staff, delivery, ratings, weather)
- **Cleaning:** 184 missing Promotion values filled as "No Promotion"; zero duplicates confirmed
- **Group comparisons:** Premium stores earn ~3× Express revenue (~5× profit); South region leads; Bengaluru top branch (₹90,732 avg revenue); Mumbai weakest
- **Correlation matrix:** Revenue ↔ Food_Cost 0.98, Customers 0.88, Marketing only 0.43; Delivery vs Rating −0.44; weather has no impact
- **8 data-driven observations** covering right-skewed revenue (skew +0.86), loss-making days, store types, regions, and true revenue drivers

## 📈 Day 14 Highlights
- **Dataset:** 360 order-batch records × 16 columns (8 cities, 6 cuisines, 3 channels, 4 weather types) — already clean (0 missing, 0 duplicates)
- **14 visualizations:** line trends, bar comparisons, histograms, scatter plots, box/violin plots, count plots and a correlation heatmap — each with interpretation
- **Biggest insight:** Delivery time vs Customer Rating correlation **−0.88** — slow delivery is the strongest destroyer of satisfaction
- **Trends & comparisons:** December best month (~₹25.4 lakh revenue); Bengaluru & Delhi top cities; Healthy cuisine highest AOV (₹501.8); App channel dominates (59% batches)
- **Weather impact:** Rainy days slow deliveries to ~38.8 min and drop ratings to 4.23 vs Clear (30 min, 4.53)

## 🏨 Day 15 Highlights
- **Dataset:** 25,180 hotel booking records × 35 columns (City/Resort hotels across 11 locations — bookings, stay details, channels, ADR, revenue, outcomes)
- **Cleaning at scale:** 22,217 missing values resolved across 8 columns (Company_ID ~82% missing → dropped), 180 duplicates removed (→ 24,999 rows), 1 impossible satisfaction score (5.9 > max 5) removed
- **Standardization:** Hotel_Type (5 messy variants), Market_Segment & Meal_Type (10 variants) cleaned; 3 date columns converted object → datetime64[ns]
- **Feature engineering:** `Arrival_Month` via `dt.month`, `Lead_Time_Bin` buckets (0–30 / 31–90 / 91–180 / 180+ days) via `pd.cut()`
- **Biggest insight:** Cancellation rate is very high (**72.18%**) — rises from 44.63% (0–30 day lead) to 85.79% (180+ days); Online TA drives ~43% of bookings; Non-refund deposits show ~93% cancellations

---

## 👤 Author

**Patel Harshilkumar Rajubhai**  
Information Technology & Data Analytics  
[GitHub](https://github.com/Harshil2992005)