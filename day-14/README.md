# 📊 Food Delivery Business Performance - Data Visualization Portfolio

**Student Name:** Patel Harshilkumar Rajubhai
**Project Track:** Day 14 Food Delivery Data Visualization Portfolio
**Dataset:** `Day14_Food_Delivery_Visualization_Dataset.csv` (360 Order Batches)

---

## 📌 Executive Summary

This project focuses on building a complete **visualization portfolio** for a Food Delivery business dataset using **Matplotlib and Seaborn**.

The main goal of this task is to explore and communicate meaningful patterns hidden inside the data by selecting the right chart type for the right question — line plots for time trends, bar charts for category comparison, scatter plots for relationships, histograms for distributions, box/violin plots for group comparisons, count plots for category frequency and a correlation heatmap to see all numeric relations together.

Every chart is supported with a short interpretation explaining the insight it reveals, and the notebook ends with a summary of the most important findings along with practical business advice.

---

## 🔍 Dataset Overview

The dataset contains **360 order batch records and 16 columns** covering different aspects of the food delivery business.

Each row represents one **order batch** (a city + cuisine + channel + weather combination).

The dataset includes:

* **Identity:** Order Batch ID, Date, Month, Day
* **Location:** City (8 cities - Bengaluru, Delhi, Hyderabad, Mumbai, Pune, Jaipur, Chandigarh, Kochi)
* **Food:** Cuisine (6 types - North Indian, South Indian, Chinese, Biryani, Healthy, Fast Food)
* **Sales Channel:** Order Channel (App, Website, Partner Platform)
* **Environment:** Weather (Clear, Cloudy, Hot, Rainy)
* **Performance Numbers:** Orders, Average Order Value, Revenue
* **Cost Factors:** Marketing Spend, Discounts
* **Service Quality:** Avg Delivery Minutes, Customer Rating
* **Loyalty:** Repeat Customer Percent

**Data Quality:** The dataset is already clean — **0 missing values**, **0 duplicate rows**, so the focus stays fully on visualization.

---

## 🛠️ Tools & Libraries Used

| Library | Purpose |
|---------|---------|
| Pandas | Loading CSV, grouping (`groupby`), sorting, aggregation |
| NumPy | Numeric support |
| Matplotlib | Line plots, bar charts, histograms, scatter plots, figure control |
| Seaborn | Box plot, violin plot, count plot, correlation heatmap |

---

## 📈 Visualizations Created

A total of **14 visualizations** were created, each chosen based on what needed to be investigated:

| # | Chart Type | What Was Investigated |
|---|-----------|----------------------|
| 1 | Line Plot | Month wise revenue trend over the year |
| 2 | Line Plot | Month wise orders trend over the year |
| 3 | Bar Chart | City wise total revenue comparison |
| 4 | Bar Chart | Cuisine wise average order value comparison |
| 5 | Histogram | Distribution of revenue per batch |
| 6 | Histogram | Distribution of customer ratings |
| 7 | Histogram | Distribution of delivery minutes |
| 8 | Scatter Plot | Marketing spend vs revenue relationship |
| 9 | Scatter Plot | Delivery time vs customer rating relationship |
| 10 | Box Plot | Weather effect on delivery time |
| 11 | Violin Plot | Customer rating distribution per cuisine |
| 12 | Count Plot | Which order channel customers use most |
| 13 | Count Plot | Weather days frequency in the data |
| 14 | Correlation Heatmap | All numeric columns relation in one view |

All charts include proper **titles, axis labels, legends and formatting** as required by the assignment.

---

## 📊 Key Findings

### 1. Time Trend - Orders & Revenue Over Months

Revenue keeps rising and falling through the year instead of growing smoothly.

- **December** is the highest revenue month (~₹25.4 lakh) — year end festival season
- **June** brings the highest number of orders (5,816 orders)
- **February** is the weakest month on both counts (2,853 orders, ~₹11.3 lakh)

Both line plots confirm each other: more orders directly means more revenue.

### 2. City Performance Comparison

Big metro cities clearly dominate the business:

- **Bengaluru** earns the most (~₹38.5 lakh), followed very closely by **Delhi** (~₹38.1 lakh)
- **Kochi** earns the least (~₹20.3 lakh) — almost half of Bengaluru

Resources like riders and kitchens should match this city-wise demand.

### 3. Cuisine Performance Comparison

- **Healthy** food has the highest average order value (**₹501.8**) and also the highest total revenue (~₹49.9 lakh)
- **Biryani** follows second (₹458.9 average order value)
- **Fast Food** is the cheapest cuisine (₹316.7 average order value) with lowest total revenue (~₹27.2 lakh)

Premium cuisines bring more money per order and deserve more promotion.

### 4. Marketing Spend vs Revenue (Scatter Plot)

Correlation is only **+0.20 (weak)** — spending more marketing money does NOT guarantee more revenue blindly. Marketing budget must be targeted into the right cities, cuisines and seasons instead of spreading everywhere.

### 5. Delivery Time vs Customer Rating (Scatter Plot) ⭐ Biggest Insight

Correlation is **-0.88 (strong negative)** — as delivery becomes slower, customer rating falls strongly and clearly.

**Fast delivery is the single biggest reason behind happy customers.**

### 6. Weather Effect on Delivery (Box Plot)

Rain directly hurts both speed and satisfaction:

| Weather | Avg Delivery Time | Avg Rating |
|---------|------------------|------------|
| Clear ☀️ | 30.0 min (fastest) | 4.53 (best) |
| Cloudy ☁️ | 31.7 min | 4.50 |
| Hot 🔥 | 32.5 min | 4.47 |
| Rainy 🌧️ | 38.8 min (slowest) | 4.23 (worst) |

Extra riders are needed on rainy days to protect customer experience.

### 7. Cuisine vs Ratings (Violin Plot)

All 6 cuisines show similar rating distributions averaging around **4.4 – 4.5**. Food type does not change satisfaction much — delivery speed matters more than the dish itself.

### 8. Order Channel Effect (Count Plot)

- **App dominates** — 211 out of 360 batches (~59%) and also gives the highest order value (₹414.3)
- **Website** comes second (77 batches)
- **Partner Platform** is the weakest channel (72 batches, ₹391.1 order value)

### 9. Correlation Heatmap Summary

| Relation | Correlation | Meaning |
|----------|-------------|---------|
| Orders ↔ Revenue | +0.76 | Orders strongly drive revenue |
| Repeat Customers ↔ Rating | +0.82 | Happy customers come back again |
| Discounts ↔ Orders | +0.40 | Discounts moderately boost orders |
| Marketing ↔ Revenue | +0.20 | Marketing alone cannot fix sales |
| Delivery Time ↔ Rating | **-0.88** | Slow delivery destroys ratings |

---

## 🎯 Conclusion

The Day 14 visualization portfolio successfully explored the Food Delivery business dataset from every important angle using the correct chart type for each question.

The analysis revealed that **December is the best month**, **Bengaluru and Delhi are the top cities**, and **Healthy/Biryani are the premium cuisines**. The strongest discovery is that **delivery time has a powerful negative relation (-0.88) with customer ratings** — even stronger than any money-related factor. Weather also plays a clear role, with rainy days slowing deliveries to ~39 minutes and dropping ratings to 4.23.

**Business advice from this analysis:** Focus on fast delivery (especially during rain and December rush), promote the App channel, push premium cuisines like Healthy and Biryani, run discount campaigns in weak months like February, and invest marketing money only in top performing cities instead of spreading it blindly.

---

## 👤 Author Information

**Student Name:** Patel Harshilkumar Rajubhai
**Topic:** Food Delivery Data Visualization Portfolio
**Project:** Day 14
