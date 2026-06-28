# 🏨 Hotel Booking Analysis

> **End-to-End Data Analytics Project**
>
> This project analyzes hotel booking data from an online travel platform to identify customer booking behavior, cancellation trends, revenue patterns, and actionable business insights using Python.

---

# 📑 Table of Contents

1. Project Overview
2. Business Problem
3. Dataset Description
4. Project Objectives
5. Tools & Libraries
6. Project Workflow
7. Data Understanding
8. Data Cleaning
9. Feature Engineering
10. Exploratory Data Analysis
11. Key Performance Indicators (KPIs)
12. Business Questions Solved
13. Visualizations
14. Key Insights
15. Root Cause Analysis
16. Business Recommendations
17. Challenges Faced
18. Learnings
19. Future Scope

---

# 📌 Project Overview

Hotels receive thousands of bookings every day through different booking channels such as websites, travel agents, and mobile applications.

However, a significant percentage of these bookings are cancelled before check-in, resulting in:

* Revenue loss
* Poor room utilization
* Inefficient pricing
* Inventory planning issues

The objective of this project is to analyze booking data and identify the major factors influencing bookings, cancellations, revenue generation, and customer behavior.

---

# 🎯 Business Problem

The company wants to answer questions like:

* Which booking channel performs best?
* Which customers cancel more frequently?
* Which room types are most preferred?
* Which hotel categories generate maximum revenue?
* During which months does demand increase?
* What are the major reasons behind booking cancellations?

The ultimate goal is to improve occupancy and maximize revenue while reducing cancellations.

---

# 📂 Dataset Description

The dataset contains booking transaction records.

### Important Columns

| Column          | Description                    |
| --------------- | ------------------------------ |
| booking_status  | Booking Completed / Cancelled  |
| booking_channel | Website, Travel Agent, etc.    |
| booking_value   | Revenue generated from booking |
| room_type       | Standard, Deluxe, Suite        |
| hotel_star      | Hotel rating                   |
| check_in_date   | Check-in date                  |
| check_out_date  | Check-out date                 |
| booking_date    | Date when booking was made     |

---

# 🛠 Tools Used

* Python
* Pandas
* NumPy
* Matplotlib
* Jupyter Notebook

---

# 📈 Project Workflow

```text
Raw Dataset
      │
      ▼
Data Inspection
      │
      ▼
Data Cleaning
      │
      ▼
Feature Engineering
      │
      ▼
Exploratory Data Analysis
      │
      ▼
KPI Calculation
      │
      ▼
Business Insights
      │
      ▼
Root Cause Analysis
      │
      ▼
Business Recommendations
```

---

# 🔍 Step 1 — Data Understanding

Before beginning analysis, I explored the dataset to understand:

```python
df.head()

df.info()

df.describe()

df.shape

df.columns
```

Purpose:

* Understand available features
* Check data types
* Identify missing values
* Identify duplicates
* Understand numerical distributions

---

# 🧹 Step 2 — Data Cleaning

### Checked Missing Values

```python
df.isnull().sum()
```

### Removed Duplicate Records

```python
df.drop_duplicates(inplace=True)
```

### Converted Date Columns

Converted booking, check-in, and check-out dates into datetime format for time-based analysis.

---

## Important Learning

Initially I used

```python
df = df.dropna()
```

This reduced the cancellation rate dramatically because many cancelled bookings had missing check-in/check-out information.

Instead of dropping every missing value, I only cleaned columns where necessary and retained cancelled bookings for accurate analysis.

**Lesson:** Never remove missing values blindly. Understand why the values are missing before cleaning.

---

# ⚙ Step 3 — Feature Engineering

Created new variables to simplify analysis.

## Month

Extracted booking month

```python
df['month'] = df['booking_date'].dt.month_name()
```

Used for:

* Monthly booking trend
* Seasonal analysis

---

## Stay Length

Calculated total stay duration

```python
df['stay_length'] = (
    df['check_out_date'] -
    df['check_in_date']
).dt.days
```

Used for:

* Average stay
* Revenue analysis

---

# 📊 Step 4 — Exploratory Data Analysis

Performed analysis on:

## Booking Status

Questions answered:

* Total completed bookings
* Total cancelled bookings

---

## Booking Channel

Analyzed:

* Total bookings
* Revenue contribution
* Cancellation rate

Purpose:

Identify the best-performing acquisition channel.

---

## Room Type

Analyzed:

* Most booked room
* Cancellation percentage
* Revenue

Purpose:

Understand customer room preference.

---

## Hotel Star Rating

Questions:

* Which hotel category receives maximum bookings?
* Which category generates highest revenue?

---

## Monthly Trends

Studied:

* Booking volume
* Revenue trend

Purpose:

Understand seasonality.

---

# 📌 Step 5 — KPI Calculation

Calculated important business metrics.

## Total Bookings

```python
df.shape[0]
```

---

## Total Revenue

```python
df['booking_value'].sum()
```

---

## Average Booking Value

```python
df['booking_value'].mean()
```

---

## Average Stay Length

```python
df['stay_length'].mean()
```

---

## Cancellation Rate

```python
cancel_rate = (
    df[df['booking_status']=="Cancelled"].shape[0]
    /
    df.shape[0]
) * 100
```

This KPI measures the percentage of bookings that were cancelled.

---

# 📊 Visualizations Created

* Monthly Booking Trend
* Monthly Revenue Trend
* Booking Status Distribution
* Booking Channel Analysis
* Room Type Analysis
* Hotel Star Analysis
* Cancellation Rate by Channel
* Revenue Distribution

---

# ❓ Business Questions Solved

### Which booking channel generated maximum bookings?

Analyzed booking counts by channel.

---

### Which booking channel generated maximum revenue?

Grouped booking values by channel.

---

### Which channel had the highest cancellation rate?

Compared cancellation percentages across channels.

---

### Which room type was most popular?

Compared booking counts.

---

### Which hotel category generated maximum revenue?

Grouped revenue by hotel star.

---

### Which months experienced peak bookings?

Analyzed booking count month-wise.

---

### Which months generated highest revenue?

Summed booking value month-wise.

---

# 💡 Key Insights

## 1. Web Channel Dominated

The Web booking channel generated the highest number of bookings and contributed the largest share of revenue.

Business implication:

Increase investment in digital marketing and website optimization.

---

## 2. Travel Agent Bookings Showed Higher Cancellation

Travel-agent bookings experienced comparatively higher cancellation rates.

Business implication:

Review cancellation policies and partner performance.

---

## 3. Standard Rooms Were Most Popular

Standard rooms attracted the highest booking volume.

Business implication:

Ensure adequate inventory and optimize pricing.

---

## 4. Four-Star Hotels Received Maximum Demand

Most bookings were concentrated among 4-star hotels.

Business implication:

This category drives the majority of business and deserves focused marketing.

---

## 5. Clear Seasonal Trends

Booking volume and revenue fluctuated by month, indicating seasonal demand.

Business implication:

Use dynamic pricing and staffing during peak/off-peak periods.

---

# 🔎 Root Cause Analysis

Possible reasons for high cancellations:

* Longer booking lead times increase cancellation likelihood.
* Certain booking channels have more flexible cancellation behavior.
* Seasonal travel uncertainty.
* Lower customer commitment on some channels.

---

# 💼 Business Recommendations

### Recommendation 1

Improve website experience since it drives the highest booking volume.

---

### Recommendation 2

Implement reminder emails/SMS before check-in to reduce cancellations.

---

### Recommendation 3

Review travel-agent agreements and cancellation policies.

---

### Recommendation 4

Apply dynamic pricing during high-demand months.

---

### Recommendation 5

Promote premium room upgrades for customers booking standard rooms.

---

# ⚠ Challenges Faced

## Challenge 1

Incorrect cancellation rate after using:

```python
df.dropna()
```

### Solution

Investigated missing values and discovered cancelled bookings contained important null values. Removed only unnecessary missing records.

---

## Challenge 2

Date columns were stored as strings.

### Solution

Converted them using pandas datetime functions.

---

## Challenge 3

Choosing meaningful KPIs.

### Solution

Focused on metrics directly linked to business performance:

* Revenue
* Booking volume
* Cancellation rate
* Stay length

---

# 📚 What I Learned

Through this project I learned how to:

* Inspect raw datasets before analysis.
* Clean data without introducing bias.
* Engineer new features from dates.
* Calculate business KPIs.
* Perform exploratory data analysis.
* Translate charts into business insights.
* Conduct root cause analysis.
* Write actionable business recommendations.

---

# 🚀 Future Improvements

Possible extensions:

* Build a cancellation prediction model using Machine Learning.
* Forecast monthly revenue.
* Segment customers based on booking behavior.
* Create an interactive Power BI dashboard.
* Develop a dynamic pricing recommendation system.

---

# 📌 Conclusion

This project demonstrates an end-to-end analytics workflow—from raw data cleaning to business recommendations. It emphasizes that successful data analysis is not just about creating charts, but about transforming data into insights that help businesses make better decisions.

> **Project Ownership**
>
> This is an independently executed end-to-end data analytics project. All stages of the analysis—from data preprocessing and exploratory analysis to deriving business insights and recommendations—were completed by me.
