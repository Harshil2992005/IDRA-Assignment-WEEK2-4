# 📊 Restaurant Branch Performance Analysis (EDA)

**Student Name:** Patel Harshilkumar Rajubhai
**Project Track:** Day 13 Restaurant Branch Performance EDA
**Dataset:** `Day13_Restaurant_Branch_Performance_Dataset.csv` (350 Records)

---

## 📌 Executive Summary

This project focuses on performing a complete **Exploratory Data Analysis (EDA)** on a Restaurant Branch Performance dataset using **Python and Pandas**.

The main goal of this analysis is to understand the patterns and relationships hidden in the day-to-day performance data of restaurant branches — covering customers, revenue, profit, marketing spend, staff count, delivery time, and customer ratings.

Different Pandas operations such as summary statistics, missing-value handling, descriptive analysis, distribution analysis, categorical comparison, and correlation analysis were used to compare performance across branches, regions, and store types, and to extract meaningful data-driven insights from the dataset.

---

## 🔍 Dataset Overview

The dataset contains **350 daily records and 22 columns** covering different aspects of restaurant branch operations.

The dataset includes:

* **Record Identity:** Record ID, Date, Day, Month
* **Location:** Branch, Region, Store Type
* **Operations:** Staff Count, Marketing Spend, Customers, Orders, Average Bill
* **Financials:** Revenue, Food Cost, Operating Cost, Profit
* **Service Quality:** Avg Delivery Time (minutes), Customer Rating
* **Environment:** Temperature, Humidity, Weather
* **Promotions:** Promotion type (Combo Deal, Loyalty Offer, Weekend Offer)

---

## 📊 Pandas Operations Used

The analysis follows a complete EDA workflow using Pandas:

* Loading the CSV dataset using `read_csv()`
* Checking dataset size using `shape`
* Inspecting structure and data types using `info()`
* Generating summary statistics using `describe()`
* Checking central tendency using `mean`, `median`, and `mode`
* Finding missing values using `isnull().sum()` and `isnull().sum().sum()`
* Handling missing values using `fillna()` (Promotion column)
* Inspecting unique counts of every column using `nunique()`
* Checking duplicate records using `duplicated().sum()`
* Measuring distribution shape using `skew()` (Revenue)
* Comparing category frequencies using `value_counts()` (Region, Promotion)
* Comparing group performance using `groupby().mean()` (Store Type, Region, Branch)
* Building a correlation matrix using `corr(numeric_only=True)` and ranking feature correlations with Revenue

---

## 📈 Key Findings

### 1. Dataset Size

The dataset contains **350 records and 22 columns**. Each record represents one day of operation for a branch, capturing operational, financial, service, and weather-related information for the year 2026 (January to June).

### 2. Missing Data

There were **184 missing values in a single column**:

- Promotion: 184 missing (out of 350 rows ≈ 53%)

Missing promotion entries represent days with no active offer, so they were filled with **"No Promotion"** using `fillna()`. After this step the dataset has **0 missing values**, confirmed using `isnull().sum().sum()`.

### 3. Duplicate Records

**0 duplicate records** were found using `duplicated().sum()`, so no rows needed to be removed.

### 4. Descriptive Statistics Highlights

- **Average Revenue:** ₹86,831.80 per record (range ₹20,540.76 – ₹194,018.92)
- **Average Profit:** ₹30,210.36 (range **−₹6,924.68 to ₹89,096.19**) — some operating days ended in a **loss**
- **Average Customers:** ~217 per day | **Average Orders:** ~187 per day
- **Average Bill:** ₹388.91
- **Avg Delivery Time:** 26.1 minutes | **Customer Rating:** 4.47 out of 5
- **Staff Count:** 5 to 24 staff members (average ~12)
- **Marketing Spend:** average ₹5,516.35 per record

### 5. Distribution Analysis

The **Revenue** column has a skewness of **+0.86**, indicating a **right-skewed distribution** — most branch-days earn moderate revenue while a smaller number of high-performing days pull the average upward.

### 6. Category Comparison

**Store Type performance (averages):**

| Store Type | Revenue | Profit | Customers |
|------------|---------|--------|-----------|
| Premium | ₹152,867.31 | ₹62,890.24 | ~299 |
| Standard | ₹87,268.67 | ₹30,630.79 | ~225 |
| Express | ₹52,327.16 | ₹12,742.14 | ~161 |

Premium stores earn nearly **3× the revenue and ~5× the profit of Express stores**.

**Region performance (averages):** South leads in both Revenue (₹88,320.22) and Profit (₹30,690.57), followed closely by North (₹86,946.94 / ₹30,625.96), while West trails (₹84,126.72 / ₹28,720.86).

**Branch performance (averages):**
- **Highest Revenue:** Bengaluru (₹90,732.12) | **Lowest Revenue:** Mumbai (₹80,779.25)
- **Lowest Profit:** Mumbai (₹26,580.99)
- **Best Rated Branch:** Pune (4.54) | **Lowest Rated Branch:** Kochi (4.42)

**Category mix:** Region — South (137), North (132), West (81); Promotion — No Promotion (184), Weekend Offer (74), Combo Deal (59), Loyalty Offer (33).

### 7. Correlation Analysis

Using `corr(numeric_only=True)`, correlations of all numerical variables with **Revenue** (sorted):

| Feature | Correlation with Revenue |
|---------|--------------------------|
| Food_Cost | 0.979 |
| Profit | 0.967 |
| Operating_Cost | 0.963 |
| Customers | 0.876 |
| Orders | 0.858 |
| Average_Bill | 0.843 |
| Staff_Count | 0.695 |
| Marketing_Spend | 0.431 |
| Avg_Delivery_Min | 0.079 |
| Customer_Rating | 0.008 |
| Temperature_C | −0.026 |
| Humidity_Percent | −0.091 |

Revenue moves almost perfectly with costs and profit, strongly with customer volume (customers, orders, bill size, staff), only moderately with marketing spend, and shows virtually **no relationship with delivery time, ratings, or weather conditions**.

### 8. Performance Snapshot

| Metric | Value |
|--------|-------|
| Records | 350 |
| Columns | 22 |
| Missing Values | 184 → 0 (after fillna) |
| Duplicate Records | 0 |
| Avg Revenue | ₹86,831.80 |
| Avg Profit | ₹30,210.36 |
| Best Performing Store Type | Premium |
| Top Branch by Revenue | Bengaluru |
| Strongest Revenue Driver | Food_Cost (r = 0.979) |

---

## 🎯 Conclusion

The Day 13 EDA successfully explored the Restaurant Branch Performance dataset and converted raw operational records into clear business insights.

The analysis showed that **Premium store types clearly outperform** Standard and Express formats, that **customer volume factors** (customers, orders, staff count, average bill) are the strongest levers of revenue, and that **marketing spend gives only moderate returns** (r ≈ 0.43). Interestingly, service quality metrics such as delivery time and customer ratings showed almost no direct link with revenue, suggesting revenue is driven more by footfall than by experience scores. Region-wise, South performed best while West lagged slightly, and among branches Bengaluru led on revenue while Mumbai remained the weakest performer with the lowest profit.

The final outcome is a well-documented EDA notebook with clean data (0 missing values, 0 duplicates), full statistical summaries, group-wise comparisons, and correlation-based evidence for every insight.

---

## 👤 Author Information

**Student Name:** Patel Harshilkumar Rajubhai
**Topic:** Restaurant Branch Performance EDA
**Project:** Day 13
