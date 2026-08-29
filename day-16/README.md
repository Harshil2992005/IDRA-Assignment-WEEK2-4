# 📊 Student Wellbeing Statistical Analysis & Probability

**Student Name:** Patel Harshilkumar Rajubhai
**Project Track:** Day 16 Student Wellbeing Statistical Analysis & Probability
**Dataset:** `Day16_Student_Wellbeing_Survey.csv` (600 Students)

---

## 📌 Executive Summary

This project focuses on performing a complete **Statistical Analysis & Probability** study on a Student Wellbeing Survey dataset using **Python, Pandas and NumPy**.

The main goal of this task is to understand the wellbeing and academic-readiness profile of university students through descriptive statistics, measures of spread, outlier detection, and an exploration of how extreme values distort summary measures. In the probability section, real-life conditions are converted into quantifiable **events** (part-time job, high stress, scholarship, exercise) and the study calculates single, joint, union and conditional probabilities, then investigates **mutual exclusivity** and **statistical independence** and finally **verifies Bayes' theorem** against a direct calculation. The notebook closes with a **normal distribution** analysis using Z-scores and the **68-95-99.7 empirical rule** on the Academic Readiness Score, and summarizes everything into 5 meaningful statistical observations.

Every step shows the relevant **formula, the Python calculation, the numerical answer, and a brief interpretation**, exactly as required by the assignment.

---

## 🔍 Dataset Overview

The dataset contains **600 student survey records and 20 columns** covering academic, lifestyle, and wellbeing information.

Each row represents one **student** and their study habits, lifestyle, finances and academic situation.

The dataset includes:

* **Identity & Academics:** Student ID, Age, Faculty, Year of Study (1–4), City
* **Living & Financial Setup:** Accommodation (Hostel/Home), Scholarship (Yes/No), Part-Time Job (Yes/No), Monthly Discretionary Spending
* **Study Environment:** Internet Quality (Good/Poor), Preferred Study Space (Library/Café/Home)
* **Study & Daily Routine:** Weekly Study Hours, Average Sleep Hours, Daily Screen Time Hours, Exercise Days Per Week, Commute Time Minutes
* **Wellbeing & Outcomes:** Stress Score, Social Activity Hours Per Week, Overall Satisfaction, Academic Readiness Score

The dataset contains **no missing values** and mixes categorical (Faculty, City, Scholarship, etc.) and numerical (hours, scores, spending) columns, making it ideal for statistical analysis.

---

## 🛠️ Tools & Libraries Used

| Library | Purpose |
|---------|---------|
| Pandas | Loading CSV, `mean`, `median`, `mode`, `quantile`, `var`, `std`, boolean event masks, `idxmax`/`idxmin` |
| NumPy | Numeric support for calculations |
| Statistics (Python) | Formulas for dispersion, IQR fences, probability rules, Z-scores, empirical rule |

---

## 📐 Statistical Operations Used

The analysis follows a complete statistics workflow using Pandas/NumPy:

* Loading the dataset with `read_csv()` and inspecting it with `head()`, `shape`, and `dtypes`
* Calculating **central tendency** — `mean()`, `median()`, `mode()` for the 5 core numerical variables
* Calculating **dispersion** — Range (`max − min`), Variance (`var()`), Standard Deviation (`std()`), Quartiles (`quantile(0.25)` and `quantile(0.75)`) and IQR (`Q3 − Q1`)
* Identifying the **variable with greatest variability** by comparing standard deviations
* Detecting **outliers** using the IQR rule — fences `Q1 − 1.5×IQR` and `Q3 + 1.5×IQR` — for 4 variables
* Comparing **mean vs median before and after removing outliers** for Monthly Discretionary Spending
* Defining **probability events** — A, B, C, D — using boolean masks on columns
* Computing `P(event)` from favourable/total counts, plus `P(A or B)`, `P(A and B)`, `P(A|B)`, `P(B|A)`
* Checking **mutual exclusivity** by computing P(Year 1 and Year 4) = 0
* Checking **independence** by comparing `P(A and B)` with `P(A) × P(B)`
* Applying **Bayes' theorem** `P(A|B) = P(B|A)·P(A) / P(B)` and verifying it against the direct conditional-probability result
* Studying the **normal distribution** — mean, std dev, Z-scores of best/worst students, and the 68-95-99.7 empirical rule coverage

---

## 📊 Key Findings

### 1. Dataset Size & Structure

The dataset contains **600 student records and 20 columns**. Each record represents one student survey answer covering identity, faculty, living setup, daily routines, wellbeing scores and academic readiness. All columns are fully populated (`0 missing values`), so no cleaning was required.

### 2. Central Tendency (Mean, Median, Mode)

Calculated for the 5 core variables:

| Variable | Mean | Median | Mode | Interpretation |
|----------|------|--------|------|----------------|
| Weekly Study Hours | 15.69 | 15.4 | 13.1 | Slight right skew — a few heavy studiers pull the mean up |
| Average Sleep Hours | 7.0 | 7.0 | 7.0 | Perfectly consistent — almost everyone sleeps ~7h |
| Daily Screen Time Hours | 4.5 | 4.2 | 3.5 | Right-skewed — heavy users stretch the average up |
| Stress Score | 4.46 | 4.5 | 4.7 | Fairly symmetric, mild everyday stress levels |
| Academic Readiness Score | 71.77 | 71.65 | 71.1 | Nearly symmetric, centered around ~72 |

### 3. Dispersion (Range, Variance, Std Dev, Q1, Q3, IQR)

| Variable | Range | Variance | Std Dev | Q1 | Q3 | IQR |
|----------|-------|----------|---------|-----|-----|-----|
| Weekly Study Hours | 30.0 | 19.22 | 4.38 | 13.0 | 18.42 | 5.42 |
| Average Sleep Hours | 5.0 | 0.70 | 0.84 | 6.48 | 7.60 | 1.12 |
| Daily Screen Time Hours | 11.2 | 3.47 | 1.86 | 3.2 | 5.4 | 2.2 |
| Stress Score | 8.4 | 2.78 | 1.67 | 3.3 | 5.7 | 2.4 |
| Academic Readiness Score | 56.1 | 93.98 | 9.69 | 65.2 | 78.03 | 12.83 |

🎯 **Variable with greatest variability: Academic Readiness Score — Std Dev = 9.69** (largest spread by far), followed by Weekly Study Hours (4.38).

### 4. Outlier Detection (IQR Method)

The IQR rule flags any value outside `Q1 − 1.5×IQR` (lower fence) to `Q3 + 1.5×IQR` (upper fence):

| Variable | Lower Fence | Upper Fence | Outliers Found |
|----------|-------------|-------------|----------------|
| Weekly Study Hours | 4.86 | 26.56 | 8 |
| Daily Screen Time Hours | −0.1 | 8.7 | 18 |
| Commute Time Minutes | −13.85 | 58.75 | 4 |
| Monthly Discretionary Spending | −1430.25 | 13351.75 | 20 |

**Monthly Discretionary Spending has the most outliers (20)** — a handful of very high spenders sit far above the typical range; screen time also has a notable 18 extreme users.

### 5. Outlier Effect on Mean vs Median

After removing the **20 outlier spenders** from Monthly Discretionary Spending (₹):

| Measure | Before | After | Change |
|---------|--------|-------|--------|
| Mean | ₹6,343.78 | ₹5,973.72 | ↓ ₹370.06 (**large drop**) |
| Median | ₹5,685.50 | ₹5,590.50 | ↓ ₹95.00 (**small change**) |

The mean is **pulled down strongly** because it uses every extreme value, while the median barely moves — proving the **median is more robust to outliers** and often the safer central measure for skewed data.

### 6. Probability — Single Events

Events defined from the data (total = 600 students):
*A = Part-Time Job "Yes", B = Stress Score ≥ 7, C = Scholarship "Yes", D = Exercise ≥ 3 days/week*

| Event | Students | Probability |
|-------|----------|-------------|
| A — part-time job | 152 | P(A) = **0.2533** |
| B — high stress | 45 | P(B) = **0.0750** |
| C — scholarship | 184 | P(C) = **0.3067** |
| D — exercise ≥ 3 days | 356 | P(D) = **0.5933** |

Only **7.5%** of students report high stress (score ≥ 7), while almost **59%** exercise at least 3 days a week.

### 7. Compound & Conditional Probability

| Expression | Value |
|-----------|-------|
| P(A and B) | 0.0517 |
| P(A or B) | 0.2767 |
| P(A\|B) | 0.6889 |
| P(B\|A) | 0.2039 |

**Interpretation:** A stressed student has a **69% chance of having a part-time job**, while a working student has only a **20% chance of high stress** — high stress is strongly linked to part-time work.

### 8. Mutually Exclusive Events

- Year of Study 1 and Year of Study 4 are compared:
  - Joint count = **0** students in both → **P(Year 1 and Year 4) = 0**
- Since `P(both) = 0`, these events **cannot happen together** → they are **MUTUALLY EXCLUSIVE** ✅

### 9. Independence Check

Independence holds only if `P(A and B) = P(A) × P(B)`:

| Check | Value |
|-------|-------|
| P(A and B) | **0.0517** |
| P(A) × P(B) | 0.2533 × 0.075 = **0.0190** |

`0.0517 ≠ 0.0190` → **Events A and B are DEPENDENT**. Having a part-time job and experiencing high stress are related, not independent.

### 10. Bayes' Theorem Verification ✅

Using the formula `P(A|B) = [P(B|A)·P(A)] / [P(B|A)·P(A) + P(B|not A)·P(not A)]`:

| Input | Value |
|-------|-------|
| P(B\|A) | 0.2039 |
| P(B\|not A) | 0.0312 |
| P(not A) | 0.7467 |

**Bayes result P(A|B) = 0.6889** and **Direct result P(A|B) = 0.6889** → both match exactly → **Bayes' theorem VERIFIED** ✅

### 11. Normal Distribution & Z-Scores

Academic Readiness Score: **Mean = 71.77, Std Dev = 9.69**

| Student | Score | Z-Score | Interpretation |
|---------|-------|---------|----------------|
| Top — STU0131 | 98.0 | **+2.71** | ~2.7 SD above average → excellent readiness |
| Lowest — STU0543 | 41.9 | **−3.08** | ~3.1 SD below average → extreme low, very rare |

**Empirical rule (68-95-99.7) coverage check:**

| Range | Expected | Actual | Match |
|-------|----------|--------|-------|
| Mean ± 1 SD | 68% | 69.5% | ✅ very close |
| Mean ± 2 SD | 95% | 95.17% | ✅ very close |
| Mean ± 3 SD | 99.7% | 99.83% | ✅ very close |

The actual coverage is almost exactly the theoretical values → the score is **approximately normally distributed**.

### 12. Key Findings Snapshot

| Metric | Value |
|--------|-------|
| Records | 600 |
| Columns | 20 |
| Missing Values | 0 |
| Most Stable Variable | Sleep Hours (SD 0.84) |
| Greatest Variability | Academic Readiness (SD 9.69) |
| Most Outliers | Monthly Spending (20) |
| Robust Measure | Median (barely moved after outlier removal) |
| Dependence Result | Part-time job & high stress → DEPENDENT |
| Mutual Exclusivity | Year 1 & Year 4 → YES (joint prob 0) |
| Bayes Verification | Match (0.6889) |
| Top Student Z-score | +2.71 |
| Lowest Student Z-score | −3.08 |

---

## 🎯 Conclusion

The Day 16 statistical analysis successfully converted the raw Student Wellbeing Survey into clear statistical evidence covering descriptive statistics, dispersion, outliers, probability and the normal distribution.

The analysis showed that **sleep is the most stable habit** (mean = median = mode = 7.0 hours with a tiny standard deviation of 0.84), while **Academic Readiness Score varies the most** (SD 9.69) and follows an almost perfect **normal distribution** — actual coverage of 69.5%, 95.17% and 99.83% matched the 68-95-99.7 rule, with the topper at Z = +2.71 and the weakest student at Z = −3.08. Outlier analysis found 8 to 20 extreme values across the four target variables and clearly demonstrated a key statistics concept: **outliers pull the mean but barely move the median**, confirming the median (₹5,590 after removal vs mean's ₹370 drop) is the robust measure.

In probability, only **7.5%** of students have high stress, part-time workers are **dependent** with stress (P(A and B) = 0.0517 ≠ 0.0190), stressed students have a 69% chance of working part-time, Year 1 and Year 4 are mutually exclusive, and **Bayes' theorem was independently verified** — both routes produced exactly P(A|B) = 0.6889.

The final outcome is a well-documented statistical notebook with a formula → Python calculation → numerical answer → interpretation flow for every task and 5 meaningful statistical observations based entirely on the data.

---

## 👤 Author Information

**Student Name:** Patel Harshilkumar Rajubhai
**Topic:** Student Wellbeing Statistical Analysis & Probability
**Project:** Day 16