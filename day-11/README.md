# 🧹 Company Employee Data Cleaning

**Student Name:** Patel Harshilkumar Rajubhai
**Project Track:** Day 11 Company Employee Data Cleaning
**Dataset:** `Day11_Messy_Company_Employee_Dataset.csv` (157 Employees)

---

## 📌 Executive Summary

This project focuses on cleaning and preparing a messy Company Employee dataset using **Python and Pandas**.

The main goal of this cleaning task is to identify and resolve common data-quality problems such as missing values, inconsistent entries, incorrect data types, and duplicate records to produce an analysis-ready dataset.

Different Pandas operations such as missing-value detection, median/mode imputation, forward/backward filling, string standardization, duplicate removal, and datetime conversion were used to transform the raw messy dataset into a clean, structured format.

---

## 🔍 Dataset Overview

The dataset contains **157 employee records and 12 columns** covering different aspects of employee information.

The dataset includes:

* **Employee Identity:** Employee ID, Employee Name
* **Organizational:** Department, Job Title
* **Demographics:** Age, Gender, City
* **Compensation:** Annual Salary, Experience Years
* **Dates:** Joining Date
* **Performance:** Performance Score
* **Work Arrangement:** Work Mode

---

## 📊 Pandas Operations Used

The cleaning follows a complete data cleaning workflow using Pandas:

* Loading the CSV dataset using `read_csv()`
* Checking dataset size using `shape`
* Inspecting columns using `columns`
* Checking data types using `info()` and `dtypes`
* Generating statistics using `describe(include='all')`
* Finding missing values using `isnull().sum()` and `isnull().sum().sum()`
* Checking duplicate records using `duplicated().sum()`
* Removing duplicate records using `drop_duplicates()`
* Handling missing numeric values using median imputation (`fillna()` with `median()`)
* Handling missing categorical values using mode imputation (`fillna()` with `mode()[0]`)
* Handling missing location/mode values using forward fill (`ffill()`) and backward fill (`bfill()`)
* Standardizing string entries using `str.strip()` and `str.title()`
* Converting date column to datetime using `pd.to_datetime()`
* Inspecting unique values using `nunique()`
* Exporting cleaned dataset using `to_csv()`

---

## 📈 Key Findings

### 1. Dataset Size

The dataset contains **157 employee records and 12 columns**. It provides information about employees, departments, compensation, demographics, performance, and work arrangements.

### 2. Missing Data

There were **32 missing values across 8 columns** in the original dataset:

- Department: 5 missing
- Gender: 5 missing
- Age: 4 missing
- Annual Salary: 5 missing
- Experience Years: 3 missing
- City: 5 missing
- Performance Score: 3 missing
- Work Mode: 2 missing

All missing values were successfully resolved using appropriate imputation strategies.

### 3. Duplicate Records

**7 exact duplicate records** were identified and removed using `drop_duplicates()`, reducing the dataset from **157 rows to 150 rows**.

### 4. Categorical Standardization

Inconsistent categorical entries were standardized:

- **Department:** Stripped whitespace, title-cased, missing filled with mode ("Marketing")
- **Gender:** Stripped whitespace, title-cased, missing filled with mode ("Male"), fixed "Other" entry
- **City:** Stripped whitespace, title-cased, missing filled using forward/backward fill
- **Work Mode:** Stripped whitespace, title-cased, missing filled using forward fill

### 5. Imputation Strategy

Appropriate imputation methods were applied based on data type:

- **Numeric columns (median):** Age (39.0), Annual Salary (₹90,046.5), Experience Years (9.35), Performance Score (4.0)
- **Categorical columns (mode):** Department ("Marketing"), Gender ("Male")
- **Sequential columns (ffill/bfill):** City, Work Mode

### 6. Datatype Fix

The **Joining_Date** column was converted from `object` (string) to proper `datetime64[ns]` datatype, enabling temporal analysis.

### 7. Before vs After Comparison

| Metric | Before Cleaning | After Cleaning |
|--------|----------------|----------------|
| Rows | 157 | 150 |
| Columns | 12 | 12 |
| Missing Values | 32 | 0 |
| Duplicate Records | 7 | 0 |
| Joining_Date Datatype | object | datetime64[ns] |

**Improvements Achieved:**
- Removed 7 duplicate records
- Resolved 32 missing values across 8 columns
- Standardized inconsistent categorical entries (Department, Gender, City, Work Mode)
- Corrected Joining_Date datatype from string to datetime
- Produced a clean dataset with **150 records × 12 columns**, **0 missing values**, **0 duplicates**

---

## 🎯 Conclusion

The Day 11 data-cleaning task successfully transformed the messy Company Employee dataset into a cleaner and analysis-ready dataset.

The process addressed missing values, duplicate records, inconsistent entries, and datatype issues. Appropriate Pandas techniques were applied based on the type of data and cleaning requirement — median imputation for numeric fields, mode imputation for categorical fields, forward/backward fill for sequential data, and string standardization for text fields.

The final dataset contains **150 rows × 12 columns** with **0 missing values** and **0 duplicate records**, ready for downstream analysis.

---

## 👤 Author Information

**Student Name:** Patel Harshilkumar Rajubhai
**Topic:** Company Employee Data Cleaning
**Project:** Day 11