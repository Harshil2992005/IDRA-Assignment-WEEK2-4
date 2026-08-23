# 🏨 Executive Hotel Booking EDA Report

**Student Name:** Patel Harshilkumar Rajubhai
**Project Track:** Day 15 Executive Hotel Booking EDA Report
**Dataset:** `Day15_Executive_Hotel_Booking_EDA_Dataset.csv` (25,180 Bookings)

---

## 📌 Executive Summary

This project performs a complete end-to-end **Exploratory Data Analysis (EDA)** on a large hotel booking dataset using **Python, Pandas, Matplotlib, and Seaborn**.

The analysis follows the full data science workflow — understanding the dataset, assessing data quality (missing values, duplicate records, incorrect data types, inconsistent values, and outliers), cleaning and preprocessing the data, and then carrying out univariate, bivariate, group-wise, and correlation analysis with rich visualizations.

Finally, the findings are translated into **5 key business insights** and **7 practical recommendations** for management decision-making.

---

## 🔍 Dataset Overview

The dataset contains **25,180 booking records and 35 columns**, where each row represents one hotel booking.

The dataset includes:

* **IDs & Dates:** Booking ID, Booking Date, Arrival Date, Reservation Status Date
* **Hotel Info:** Hotel Type (City/Resort), Hotel Location (11 cities)
* **Stay Details:** Lead Time Days, Weekend/Weekday Nights, Adults, Children, Babies, Total Nights, Room Types, Meal Type
* **Business Info:** Market Segment, Distribution Channel, Deposit Type, Customer Type, Agent ID, Company ID, ADR, Estimated Revenue
* **Outcome:** Reservation Status (Check-Out/Canceled/No-Show), Is Canceled, Satisfaction Score

---

## 📊 Pandas Operations Used

The analysis follows a complete EDA workflow using Pandas:

* Loading the CSV dataset using `read_csv()`
* Checking dataset size using `shape`
* Checking data types using `info()` and `dtypes`
* Generating statistics using `describe().T`
* Finding missing values using `isnull().sum()`
* Checking duplicate records using `duplicated().sum()`
* Inspecting categories using `value_counts()`
* Detecting invalid values using filtering (`Satisfaction_Score > 5`)
* Detecting outliers using the IQR method (`quantile()`)
* Visualizing outliers using Seaborn `boxplot()`
* Checking extreme values using `nlargest()` and `max()`
* Removing duplicates using `drop_duplicates()`
* Standardizing text entries using `str.strip()`, `str.title()`, and `str.upper()`
* Fixing inconsistent names using `replace()`
* Dropping an unusable column using `drop(columns=["Company_ID"])`
* Handling missing values using `fillna()` with `"Unknown"`, `0`, and `median()`
* Converting dates using `pd.to_datetime()`
* Creating new features using `dt.month` and `pd.cut()` (lead-time bins)
* Group-wise analysis using `groupby()` with `mean()`
* Pivot table analysis using `pivot_table()`
* Correlation analysis using `corr()`

---

## 📈 Visualizations Created (Matplotlib & Seaborn)

* **Histograms:** Lead Time, ADR, Total Nights, Satisfaction Score distributions
* **Count Plots:** Reservation Status, Deposit Type, Customer Type, Market Segment
* **Bar Charts:** Top 10 Hotel Locations, Cancellation Rate by Segment/Deposit/Lead Time, Average Price by Location, Satisfaction by Hotel Type
* **Pie Chart:** City Hotel vs Resort share
* **Box Plots:** ADR outlier check, Revenue outlier check
* **Line Plot:** Monthly bookings vs cancellations trend
* **Heatmaps:** Revenue by Location × Month (group-wise), Correlation matrix of numeric columns

---

## 📈 Key Findings

### 1. Dataset Size

The dataset contains **25,180 booking records and 35 columns** covering booking dates, stay details, business channels, revenue, and reservation outcomes.

### 2. Missing Data

There were **22,217 missing values across 8 columns** in the original dataset:

- Company_ID: 20,729 missing (~82% — column dropped)
- Country: 466 missing → filled with "Unknown"
- Agent_ID: 304 missing → filled with 0 (no agent)
- Meal_Type: 245 missing → filled with "OTHER"
- Satisfaction_Score: 164 missing → filled with median
- Children: 121 missing → filled with median
- Hotel_Location: 106 missing → filled with "Unknown"
- ADR: 82 missing → filled with median

All missing values were successfully resolved using appropriate strategies.

### 3. Duplicate Records

**180 exact duplicate records** were identified and removed using `drop_duplicates()`, reducing the dataset from **25,180 rows to 25,000 rows**.

### 4. Categorical Standardization

Inconsistent categorical entries were standardized:

- **Hotel_Type:** 5 messy variants (`CITY HOTEL`, `city hotel`, `City hotel`) merged into clean categories using `str.strip()` + `str.title()`
- **Market_Segment:** Trailing spaces and letter case fixed (e.g., `Online TA ` → `Online Ta`)
- **Meal_Type:** 10 messy variants (`BB `, `bb`, ` B&B `, `Undefined`, `Unknown`) cleaned into BB / HB / FB / SC / OTHER using `str.upper()` + `replace()`

### 5. Invalid Values & Outliers

- **Impossible satisfaction score found:** max value was **5.9** (valid range is 1–5) → those rows were removed after detection using `data[data["Satisfaction_Score"] > 5]`
- **ADR outliers detected:** max price **710.5** vs median **134.43** using IQR method and boxplot
- **Extreme lead time flagged:** maximum **920 days (~2.5 years)** checked using `nlargest()`

### 6. Datatype Fix

Three date columns (**Booking_Date, Arrival_Date, Reservation_Status_Date**) were converted from `object` (string) to proper `datetime64[ns]` datatype, enabling time-based analysis.

### 7. Feature Engineering

Two new analysis-friendly columns were created:

- **Arrival_Month:** extracted using `dt.month` for monthly trend analysis
- **Lead_Time_Bin:** lead-time buckets (0–30, 31–90, 91–180, 180+ days) created using `pd.cut()`

### 8. Key Business Insights

- **Cancellation rate is very high: 72.18%** (16,723 Canceled + 1,451 No-Show out of 25,180)
- **Online TA dominates:** ~43% of all bookings come from this single segment (10,934 bookings)
- **Longer lead time means more cancellations:** cancel rate rises from **44.63%** (0–30 days) to **85.79%** (180+ days)
- **Non-refund deposits show ~93% cancellations** — an unexpected pattern that needs investigation
- **Top locations are close competitors:** Dubai (3,171), Lisbon (3,168), London (3,130) bookings

### 9. Before vs After Comparison

| Metric | Before Cleaning | After Cleaning |
|--------|----------------|----------------|
| Rows | 25,180 | 24,999 |
| Columns | 35 | 36* |
| Missing Values | 22,217 | 0 |
| Duplicate Records | 180 | 0 |
| Impossible Scores (>5) | Present | Removed |
| Date Columns Datatype | object | datetime64[ns] |

*\*Company_ID dropped (−1), Arrival_Month and Lead_Time_Bin added (+2)*

**Improvements Achieved:**
- Removed 180 duplicate records and 1 impossible satisfaction record
- Resolved all 22,217 missing values across 8 columns
- Standardized inconsistent categorical entries (Hotel_Type, Market_Segment, Meal_Type)
- Corrected 3 date columns from string to datetime
- Produced a clean dataset ready for reliable analysis

---

## 🎯 Conclusion

The Day 15 project successfully performed a complete end-to-end EDA on the Executive Hotel Booking dataset.

The workflow covered data understanding, quality assessment, cleaning, univariate/bivariate/group-wise/correlation analysis, and visualization using Matplotlib and Seaborn. The most critical business finding is the very high cancellation rate (**72.18%**), strongly linked to long lead times and heavy dependency on online travel agents.

The final deliverable is a professional Jupyter notebook with quantified insights and practical recommendations that management can act on directly.

---

## 👤 Author Information

**Student Name:** Patel Harshilkumar Rajubhai
**Topic:** Executive Hotel Booking EDA Report
**Project:** Day 15
