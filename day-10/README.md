# ✈️ Flight Operations Data Analysis

**Student Name:** Patel Harshilkumar Rajubhai
**Project Track:** Day 10 Flight Operations Data Analysis
**Dataset:** `Day10_Flight_Operations_Dataset.csv` (180 Flights)

---

## 📌 Executive Summary

This project focuses on analyzing a Flight Operations dataset using **Python and Pandas**.

The main goal of this analysis is to understand flight operations, ticket pricing, delays, passenger satisfaction, weather conditions, and route performance.

Different Pandas operations such as filtering, sorting, grouping, aggregation, missing-value handling, and data transformation were used to find useful patterns from the dataset.

---

## 🔍 Dataset Overview

The dataset contains **180 flight records and 17 columns** covering different aspects of flight operations.

The dataset includes:

* **Flight Details:** Flight ID, Flight Date, Airline, Origin, Destination
* **Aircraft Details:** Aircraft Type and Travel Class
* **Passenger Details:** Passengers, Seat Capacity and Average Baggage
* **Pricing:** Average Ticket Price
* **Operations:** Delay Minutes and Flight Status
* **External Factors:** Weather
* **Booking:** Booking Channel
* **Customer Experience:** Meal Preference and Passenger Satisfaction

---

## 📊 Pandas Operations Used

The analysis follows a complete data analysis workflow using Pandas:

* Loading the CSV dataset using `read_csv()`
* Checking dataset size using `shape`
* Inspecting columns using `columns`
* Checking data types using `info()` and `dtypes`
* Generating statistics using `describe()`
* Finding missing values using `isnull()`
* Handling missing delay values using median imputation
* Checking and removing duplicate records
* Selecting relevant columns
* Filtering flights using multiple conditions
* Sorting flights by ticket price and delay
* Grouping data by routes and weather
* Performing aggregation using `count()`, `sum()` and `mean()`
* Converting flight dates into datetime format
* Creating a Load Factor column
* Extracting month information from flight dates

---

## 📈 Key Findings

### 1. Dataset Size

The dataset contains **180 flight records and 17 columns**. It provides information about flights, airlines, passengers, pricing, delays, weather and customer satisfaction.

### 2. Missing Data

There were **7 missing values in `Delay_Minutes`**. These values were handled using the median delay before continuing with the analysis.

### 3. Ticket Price

The average ticket price is around **₹6,112**.

The cheapest ticket in the dataset was **₹1,949**, while the most expensive ticket was **₹27,832**.

Business class had much higher average ticket prices compared with Economy and Premium Economy.

### 4. Flight Delays

The average delay was around **19 minutes**.

There were **18 flights with delays above 50 minutes**, and the maximum recorded delay was **110 minutes**.

### 5. Airline Performance

Vistara had the highest number of flights in the dataset with **37 flights**.

IndiGo had the highest average delay among the airlines at around **25 minutes**, showing a noticeable difference in delay performance between airlines.

### 6. Route Performance

**Delhi to Chennai** was the busiest route with **17 flights**.

The **Hyderabad to Kolkata** route had the highest average delay in the route analysis, at approximately **51.7 minutes**.

### 7. Weather and Delays

Rain had the highest average delay at around **21.4 minutes**.

Passenger satisfaction was highest during Cloudy weather at around **3.84**, while Storm had the lowest satisfaction at around **3.17**.

### 8. Load Factor

The overall average load factor was around **62.7%**.

This means that, on average, flights were using around 63% of their available seating capacity.

---

## 🎯 Conclusion

The analysis shows that flight operations can vary significantly depending on the airline, route, weather condition and travel class.

Ticket prices were strongly different across travel classes, while delays varied between airlines and routes. Weather conditions also showed differences in average delays and passenger satisfaction.

The Load Factor transformation provided an additional way to understand how effectively available aircraft seating capacity was being used.

Overall, Pandas helped turn the raw flight dataset into useful information about **pricing, delays, routes, airline performance and passenger experience**.

---

## 👤 Author Information

**Student Name:** Patel Harshilkumar Rajubhai
**Topic:** Flight Operations Data Analysis
**Project:** Day 10
