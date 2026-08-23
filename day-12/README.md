# 🛠️ Used Car Resale Price – Data Preprocessing

**Student Name:** Patel Harshilkumar Rajubhai
**Project Track:** Day 12 Used Car Data Preprocessing
**Dataset:** `Day12_Used_Car_Preprocessing_Dataset.csv` (320 Used Cars)

---

## 📌 Executive Summary

This project focuses on preparing a Used Car Resale dataset for machine learning using **Python, Pandas, and Scikit-learn**.

The main goal of this preprocessing task is to convert the raw car listing data into a clean, model-ready dataset by handling outliers with the IQR method, encoding categorical variables (both ordinal and nominal), and scaling numeric features using standardization.

Special care was taken to avoid data leakage — the dataset was split into training and testing sets first, and every fitted transformation (scaler, encoder, outlier bounds) was learned **only from the training data** and then applied to both sets.

---

## 🔍 Dataset Overview

The dataset contains **320 used-car records and 15 columns** covering Indian used-car listings.

The dataset includes:

* **Identity:** Car_ID
* **Vehicle Specs:** Year, Mileage_Km, Engine_CC, Power_BHP
* **Categorical:** Brand, Fuel_Type, Transmission, City, Seller_Type
* **Quality Rating:** Condition (Poor < Fair < Good < Very Good < Excellent)
* **Car History:** Previous_Owners, Accidents_Reported, Service_Score
* **Target Variable:** Resale_Price_Lakh

Data quality checks:

* Missing values: **0**
* Duplicate rows: **0**

---

## 🛠️ Operations Used

The preprocessing follows a complete workflow using Pandas and Scikit-learn:

* Loading the CSV dataset using `read_csv()`
* Inspecting structure using `shape`, `info()`, and `describe()`
* Checking missing values using `isnull().sum()` and duplicates using `duplicated().sum()`
* Ordinal encoding of `Condition` using an ordered dictionary mapping (`replace()`, re-run-safe)
* Separating features (X) and target (y) and dropping `Car_ID` as a pure identifier
* Splitting data using `train_test_split()` (80% train / 20% test, `random_state=42`)
* Outlier detection using IQR method (`quantile()` based lower and upper fences) computed on **training data only**
* Handling outliers using **clipping (capping)** via `clip()` instead of deleting rows
* Scaling numeric features using `StandardScaler` (`fit_transform()` on train, `transform()` on test)
* Encoding nominal categories using `OneHotEncoder(drop='first', handle_unknown='ignore')`
* Rebuilding feature DataFrames using `get_feature_names_out()` and `np.hstack()`
* Combining train and test sets and exporting using `to_csv()`
* Verifying the final dataset (shape, nulls, dtypes, scaling statistics)

---

## 📈 Key Findings

### 1. Dataset Size and Quality

The dataset contains **320 records × 15 columns**. There were **no missing values and no duplicate records**, so no imputation or de-duplication was needed — the focus stayed fully on outlier handling, encoding, and scaling.

### 2. Ordinal Encoding of Condition

The `Condition` column contains **5 ordered quality levels**, which were mapped preserving the ranking:

| Level | Cars Encoded |
|-------|--------------|
| Poor → 0 | 15 |
| Fair → 1 | 34 |
| Good → 2 | 138 |
| Very Good → 3 | 96 |
| Excellent → 4 | 37 |

Ordinal mapping was chosen over one-hot because condition has a natural order. The mapping was applied before splitting since it uses a fixed dictionary (no statistics learned from data = no leakage risk), and it is re-run safe.

### 3. Train-Test Split (Leakage Prevention)

Target separated as `Resale_Price_Lakh`; `Car_ID` dropped as identifier. Split done **before any fitted transformation**:

| Set | Rows | Purpose |
|-----|------|---------|
| Training | 256 (80%) | Fit scaler, encoder, outlier bounds |
| Testing | 64 (20%) | Transformed only |

### 4. Outlier Detection and Handling (IQR Method)

IQR fences were computed on the **training set only** and outliers were flagged per column:

| Column | Lower Fence | Upper Fence | Outliers Flagged |
|--------|-------------|-------------|------------------|
| Mileage_Km | −31,351.75 | 175,124.25 | 2 |
| Engine_CC | 66.00 | 2,592.00 | 6 |
| Power_BHP | 67.46 | 233.36 | 5 |
| Service_Score | 35.38 | 116.38 | 0 |

Instead of dropping rows (losing records), extreme values were **clipped to the IQR fences** using `clip()`. This keeps all 320 cars while limiting the influence of extreme values. Fences learned from train were applied to both sets consistently.

### 5. Feature Scaling (Standardization)

All 8 numeric/ordinal columns (`Year`, `Mileage_Km`, `Engine_CC`, `Power_BHP`, `Condition`, `Previous_Owners`, `Accidents_Reported`, `Service_Score`) were standardized with `StandardScaler`. Verification confirmed mean ≈ 0 (range −0.04 to 0.05) and std ≈ 1 (range 0.99 to 1.02) across all scaled columns.

### 6. Nominal Encoding (One-Hot)

The 5 nominal columns (`Brand`, `Fuel_Type`, `Transmission`, `City`, `Seller_Type`) were encoded using `OneHotEncoder(drop='first')`, producing **24 dummy features** while avoiding the dummy-variable trap. Unknown categories in test data are handled safely via `handle_unknown='ignore'`.

### 7. Final Processed Dataset

After preprocessing, the feature space grew from **14 raw features to 32 features** (8 numeric/ordinal + 24 one-hot dummies). Combined with the target, the exported deliverable contains:

| Metric | Raw Dataset | Preprocessed Dataset |
|--------|-------------|----------------------|
| Rows | 320 | 320 (256 train + 64 test) |
| Columns | 15 | 33 (32 features + 1 target) |
| Missing Values | 0 | 0 |
| Text/Object Columns | 7 | 0 (fully numeric) |
| Feature Scale | Mixed raw units | Mean ≈ 0, Std ≈ 1 |

**Improvements Achieved:**
- Preserved all 5 ordered quality levels of Condition through ordinal encoding
- Detected 13 outlier values and capped them without losing any record
- Zero data leakage — every fitted transform learned from training data only
- Produced a fully numeric, model-ready dataset saved as `preprocessed_used_cars.csv`

---

## 🎯 Conclusion

The Day 12 preprocessing task successfully converted the raw Used Car Resale dataset into a clean, leakage-free, model-ready format.

Every step followed best practices: ordinal variables were rank-encoded, nominal variables were one-hot encoded with the dummy trap avoided, IQR-based outlier capping preserved all 320 records while neutralizing extremes, and standardization brought all numeric features to a comparable scale. Because the split was performed before fitting any transformer, the processed test set honestly represents unseen data.

The final dataset (**320 rows × 33 columns**, zero NaNs, fully numeric, verified scaling) is exported as `preprocessed_used_cars.csv` and is ready for regression modeling of resale prices.

---

## 📁 Files

| File | Description |
|------|-------------|
| `IDRA DAY 12.ipynb` | Full preprocessing notebook with decisions documented |
| `Day12_Used_Car_Preprocessing_Dataset.csv` | Original raw dataset |
| `preprocessed_used_cars.csv` | Final processed dataset (deliverable) |

---

## 👤 Author Information

**Student Name:** Patel Harshilkumar Rajubhai
**Topic:** Data Preprocessing – Outliers, Encoding, Scaling, Train-Test Split
**Project:** IDRA Day 12
