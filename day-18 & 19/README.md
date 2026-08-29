# 📊 Student Academic Performance Prediction — ML (Regression + Classification)

**Student Name:** Patel Harshilkumar Rajubhai
**Project Track:** Day 18 & 19 Student Performance Prediction using Machine Learning
**Dataset:** `Day18_19_student_habits_performance.csv` (1000 Students)

---

## 📌 Executive Summary

This project focuses on building a complete **Machine Learning pipeline** to predict student exam scores (regression) and classify whether a student will **Pass or Fail** (classification), using study habits, lifestyle and background features.

The main goal is to understand **which factors actually drive academic performance** and then turn that understanding into working prediction models. The notebook first performs a full **Exploratory Data Analysis (EDA)** — distributions, relationships, correlations, missing values, outliers and category comparisons — to inspect the data before modeling. The features are then prepared for ML (dropping IDs, converting categorical columns with `get_dummies`), split into training/testing sets, and used to train a **Linear Regression** model for score prediction. The same data is reused to build a **Logistic Regression** Pass/Fail classifier.

Every model is evaluated properly: regression uses **MAE, MSE, RMSE and R2**, and classification uses **Confusion Matrix, Accuracy, Precision, Recall and F1-Score** — plus a training-vs-testing comparison to check for **overfitting**. The notebook ends with the key EDA findings and **5 meaningful, evidence-based insights** about student performance.

---

## 🔍 Dataset Overview

The dataset contains **1000 student records and 16 columns** covering study habits, lifestyle choices and their final exam results.

Each row represents one **student** with their background, daily routine and academic outcome.

The dataset includes:

* **Identity & Demographics:** Student ID, Age, Gender
* **Study Habits:** Study Hours Per Day, Attendance Percentage
* **Screen Time:** Social Media Hours, Netflix Hours
* **Daily Lifestyle:** Sleep Hours, Diet Quality, Exercise Frequency, Part-Time Job
* **Background & Environment:** Parental Education Level, Internet Quality
* **Wellbeing & Activities:** Mental Health Rating, Extracurricular Participation
* **Target Variable:** Exam Score

**Data Quality:** The dataset is nearly clean — only **91 missing values in `parental_education_level`**, filled with the most common category (mode) using `fillna()`. Outlier analysis found a few mild extremes (maximum 7 outliers, in study hours) which were kept as-is since nothing was extreme enough to distort the analysis.

---

## 🛠️ Tools & Libraries Used

| Library | Purpose |
|---------|---------|
| Pandas | Reading CSV, `info()`, `describe()`, `isnull()`, `fillna()`, `groupby()`, `get_dummies()`, `corr()` |
| NumPy | Numeric support, RMSE calculation (`np.sqrt`) |
| Matplotlib | Histograms (data distributions), box plots (outliers) |
| Seaborn | Correlation heatmap |
| Scikit-learn | `train_test_split`, LinearRegression, LogisticRegression, MAE/MSE/R2/confusion matrix/accuracy/precision/recall/F1 metrics |

---

## 🤖 Machine Learning Operations Used

The analysis follows a complete ML workflow using Pandas + Scikit-learn:

* Loading the dataset using `read_csv()` and previewing it with `head()`
* Inspecting structure and data types using `info()` and `describe()`
* Finding missing values using `isnull().sum()` (91 nulls found)
* Handling missing values using `fillna(data["parental_education_level"].mode()[0])`
* Checking EDA — numeric columns with `select_dtypes()`, separating numeric vs object columns
* Plotting **histograms** of every numeric column to see distributions
* Building a **correlation heatmap** (`corr()`) and ranking correlations with `exam_score`
* Detecting **outliers** using box plots and the **IQR method** per column
* Comparing **average exam scores across categories** using `groupby().mean()`
* Preparing features with `get_dummies()` on categorical columns and dropping `student_id`
* Splitting data using `train_test_split()` (80/20, `random_state=42`)
* Training **Linear Regression** and predicting exam scores
* Evaluating with **MAE, MSE, RMSE, R2** and comparing train vs test R2 for overfitting
* Converting exam scores to **Pass (≥50) / Fail** labels
* Splitting for classification with `stratify=y_class` to keep the class ratio
* Training **Logistic Regression** and evaluating with **Confusion Matrix, Accuracy, Precision, Recall, F1**
* Comparing training vs testing accuracy for a final fit assessment

---

## 📊 Key Findings — EDA

### 1. Dataset Size & Structure

The dataset contains **1000 student records and 16 columns** (1 ID, 15 features including the target). It mixes numeric (age, hours, percentages, scores) and categorical (gender, part-time job, internet quality, etc.) data with no duplicate or extreme issues.

### 2. Missing Data

- **`parental_education_level`** had **91 missing values** (≈9% of rows).
- Filled with the **mode** (most common value) using `fillna()`.
- After this step the dataset has **0 missing values**.

### 3. Distribution of Exam Scores & Features

Histograms were plotted for every numeric column. Most habit variables show realistic right-skewed distributions (a few students study very long, most study a moderate amount), while `exam_score` is centered near the 65–75 range consistent with the mean of ~70.

### 4. What Matters Most — Correlation with Exam Score

| Feature | Correlation with Exam Score | Strength |
|---------|---------------------------|----------|
| **Study Hours Per Day** | **+0.825** | 🟢 Very Strong |
| Mental Health Rating | +0.322 | 🟡 Moderate |
| Exercise Frequency | +0.160 | 🟡 Weak |
| Sleep Hours | +0.122 | 🟡 Weak |
| Attendance Percentage | +0.090 | ⚪ Very Weak |
| Age | −0.009 | ⚪ None |
| Social Media Hours | −0.167 | 🟠 Weak Negative |
| **Netflix Hours** | **−0.172** | 🟠 Weak Negative |

🎯 **Study hours is the #1 driver (r = +0.83)** — clearly above every other factor. The only negative influences are screen time (social media and Netflix).

### 5. Outlier Detection

| Column | Outliers |
|--------|----------|
| Age | 0 |
| Study Hours | **7** |
| Social Media | 5 |
| Netflix | 4 |
| Attendance | 3 |
| Sleep | 2 |
| Exercise | 0 |
| Mental Health | 0 |
| Exam Score | 2 |

Data is clean — the maximum is **7 outliers in study hours** (heavy studiers), nothing extreme enough to require removal.

### 6. Do Demographics Matter? (Category Averages)

Average exam score by group:

| Category | Average Score |
|----------|---------------|
| Gender — Female | 69.74 |
| Gender — Male | 69.37 |
| Gender — Other | 70.65 |
| Part-Time Job — No | 69.84 |
| Part-Time Job — Yes | 68.74 |
| Internet — Average | 70.64 |
| Internet — Good | 68.65 |
| Internet — Poor | 69.72 |
| Extracurricular — No | 69.59 |
| Extracurricular — Yes | 69.62 |

All groups score within ~2 marks of each other → **demographics barely matter; habits (especially studying) drive the score.**

---

## 🤖 Key Findings — Modeling

### 7. Data Preparation for ML

- Dropped `student_id` (pure ID, no predictive value).
- Converted all categorical columns with `get_dummies()` (gender, part-time job, internet quality, etc.) into numeric 0/1 columns.
- Features (`X`) vs target (`y = exam_score`) separated.
- Train/test split: **80% train / 20% test** with `random_state=42` → 800 training, 200 testing rows.

### 8. Regression Model — Linear Regression

Predicted marks for 5 unseen students: `[66.2, 75.1, 78.1, 73.3, 61.0]`

| Metric | Value | Meaning |
|--------|-------|---------|
| MAE | **4.19 marks** | Average mistake per prediction — under 5 marks |
| MSE | 26.53 | Squared-error average (penalizes big mistakes) |
| RMSE | **5.15 marks** | Typical prediction error in original units |
| R2 (Test) | **0.897** | We explain **89.7%** of score differences |

**Interpretation:** the model predicts exam marks to within ±5 marks on average, and explains ~90% of the variation in scores — a very strong regression fit.

### 9. Overfitting Check (Regression)

| Set | R2 |
|-----|-----|
| Training | 0.902 |
| Testing | 0.897 |
| Gap | **0.006** |

Gap is only 0.006, far below the 0.10 warning level → **good fit, NO overfitting** ✅ The model generalizes well to unseen students.

### 10. Classification Setup — Pass / Fail

- `exam_score >= 50` → **Pass (1)**, below 50 → **Fail (0)**.
- Full dataset: **869 students passed, 131 failed** (~87% pass rate).
- Split done with `stratify=y_class` so training and test sets keep the same ~87/13 pass-fail ratio.

### 11. Classification Model — Logistic Regression

Confusion Matrix (test set, 200 rows):

| | Predicted Fail | Predicted Pass |
|--|----------------|----------------|
| **Actual Fail** | 22 | 4 |
| **Actual Pass** | 4 | 170 |

| Metric | Value | Meaning |
|--------|-------|---------|
| Accuracy | **0.960** | 96% of predictions correct |
| Precision | **0.977** | Of predicted passes, 97.7% really passed |
| Recall | **0.977** | Of actual passers, 97.7% were caught |
| F1-Score | **0.977** | Balanced harmonic mean of precision & recall |

Only **4 students were missed** by the classifier — near-perfect Pass/Fail prediction.

### 12. Overfitting Check (Classification)

| Set | Accuracy |
|-----|----------|
| Training | 0.955 |
| Testing | 0.960 |

Testing accuracy is actually slightly higher than training (diff < 0.05) → **good fit, no significant overfitting** ✅

### 13. Final Performance Snapshot

| Metric | Value |
|--------|-------|
| Records | 1000 |
| Columns | 16 |
| Missing Values | 91 → 0 (since `fillna`) |
| Strongest Score Driver | Study Hours (r = +0.825) |
| Regression R2 (Test) | 0.897 |
| Regression Train-Test Gap | 0.006 |
| Classification Accuracy | 0.960 |
| Classification F1 | 0.977 |

---

## 💡 The 5 Meaningful Insights

1. **Study hours are the #1 predictor** — the strongest correlation (+0.83) with exam score; increasing daily study time is the single most effective change a student can make.
2. **Screen time drags scores down** — social media (−0.167) and Netflix (−0.172) are the only factors that consistently co-exist with lower marks.
3. **Habits matter more than demographics** — gender, part-time job, internet quality and extracurriculars barely changed average scores (all within ~2 marks), while study habits moved results dramatically.
4. **The model is strong and safe** — about 90% accuracy in predicting exact marks (R2 = 0.897) and 96% for Pass/Fail, with no signs of overfitting on either model.
5. **Good mental health and exercise help a little** — both had a positive, modest correlation with scores; a balanced routine (sleep + exercise + mental wellbeing) supports performance alongside studying.

---

## 🎯 Conclusion

The Day 18 & 19 ML project successfully built, evaluated and explained a complete prediction pipeline for student performance, moving from raw CSV data to two working models.

The EDA revealed that **study hours are by far the strongest predictor** (correlation +0.83, more than double the next factor), screen time is the only consistent negative influence, and demographics make almost no difference — confirming that **habits, not background, decide academic results**. Missing data (91 nulls) was handled cleanly with the mode, and outliers were confirmed mild (max 7).

Linear Regression predicted exam scores with an **R2 of 0.897** and an average error of just **4.19 marks**, with a training-testing gap of only 0.006 → no overfitting. Logistic Regression classified Pass/Fail with **96% accuracy and 0.977 F1**, missing only 4 students on the test set, again with no overfitting (0.955 train vs 0.960 test).

The final outcome is a clean, well-documented ML notebook covering the complete workflow — EDA, data preparation, regression, classification, evaluation metrics, overfitting checks and 5 meaningful, evidence-based insights — ready for submission.

---

## 👤 Author Information

**Student Name:** Patel Harshilkumar Rajubhai
**Topic:** Student Performance Prediction — ML (Regression + Classification)
**Project:** Day 18 & 19