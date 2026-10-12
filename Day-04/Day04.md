# Day 4: Descriptive Statistics & Exploratory Data Analysis (EDA)

# 60-Day Data Analyst Challenge — Phase 1



# Learning Objectives

* Different types of data used in data analysis.
* The difference between categorical and numerical data.
* Discrete and continuous numerical data.
* Descriptive statistics and their importance.
* Mean, median, and mode.
* Minimum, maximum, and range.
* Basic Exploratory Data Analysis (EDA).
* How to identify and investigate outliers.
* How to use Excel formulas to summarize data.
* How to interpret statistics from a business perspective.


# 1. Understanding Data Types

Data types describe the kind of information stored in a dataset. Understanding data types helps analysts choose the correct calculations and analysis techniques.

# 1.1 Categorical Data

Categorical data represents groups, labels, or classifications.

*Examples:*

* Product: Laptop, Mouse, Keyboard
* City: Hyderabad, Bengaluru, Chennai
* Department: Sales, Marketing, Finance
* Payment Method: UPI, Cash, Card

*Business Example:*

A company wants to identify which product category generates the most sales. A Data Analyst can group records by product and compare their revenue or quantities.

*Important:* Numeric-looking identifiers, such as customer IDs and order IDs, are usually categorical identifiers rather than measurable quantities.

# 1.2 Numerical Data

Numerical data represents quantities that can be counted or measured.

There are two main types.

# A. Discrete Data

Discrete data contains countable values, usually whole numbers.

*Examples:*

* Number of customers
* Number of orders
* Number of products sold
* Number of employees

*Business Question:* How many orders did the company receive today?

# B. Continuous Data

Continuous data represents measurements that can take decimal values within a range.

*Examples:*

* Delivery time: 2.5 hours
* Product weight: 1.75 kg
* Distance: 12.6 km
* Temperature: 32.5°C

*Business Question:* What is the average delivery time?

# Why Are Data Types Important?

Data types help analysts decide how to summarize, visualize, and interpret data.

| Data Type   | Example          | Possible Analysis                |
| ----------- | ---------------- | -------------------------------- |
| Categorical | Product Name     | Group products and compare sales |
| Discrete    | Number of Orders | Count orders                     |
| Continuous  | Delivery Time    | Calculate average delivery time  |
| Identifier  | Customer ID      | Identify unique customers        |



# 2. Descriptive Statistics

Descriptive statistics is a branch of statistics used to summarize and describe the main characteristics of a dataset.

Instead of reviewing every record individually, analysts use statistical measures to understand the overall data.

# Sample Dataset

Consider the following daily sales values:

| Day       | Sales (₹) |
| --------- | --------: |
| Day 1     |       100 |
| Day 2     |       200 |
| Day 3     |       200 |
| Day 4     |       300 |
| Day 5     |       700 |
| **Total** | **1,500** |

We will use this dataset to understand descriptive statistics.

# 2.1 Mean (Average)

The mean is the arithmetic average of all values in a dataset.

*Formula:*

Mean = Sum of all values / Number of values

*Calculation:*

Mean = (100 + 200 + 200 + 300 + 700) / 5

Mean = 1,500 / 5

*Mean = ₹300*

*Excel Formula:*

excel
=AVERAGE(B2:B6)


*Business Application:*

A sales manager can calculate average daily sales to compare performance between weeks or months.

*Limitation:* The mean can be affected by unusually high or low values.

# 2.2 Median

The median is the middle value when data is arranged in ascending or descending order.

Dataset:

100, 200, 200, 300, 700

The middle value is 200.

*Median = ₹200*

*Excel Formula:*

excel
=MEDIAN(B2:B6)


*Business Application:*

The median is useful when data contains extreme values, such as unusually high salaries or large sales transactions.

For example, if five salaries are ₹15,000, ₹18,000, ₹20,000, ₹22,000, and ₹1,50,000, the median is ₹20,000. The average is ₹45,000.

This shows why the median can sometimes better represent a typical observation.

# 2.3 Mode

The mode is the value that occurs most frequently in a dataset.

Dataset:

100, 200, 200, 300, 700

The value 200 occurs twice, while every other value occurs once.

*Mode = ₹200*

*Excel Formula:*

excel
=MODE.SNGL(B2:B6)


*Business Application:*

A retailer can use the mode to identify the most frequently purchased product size or the most common customer response.

A dataset can have multiple modes or no unique mode.

# Comparison of Mean, Median, and Mode

| Statistic | Meaning             | Result |
| --------- | ------------------- | -----: |
| Mean      | Arithmetic average  |   ₹300 |
| Median    | Middle value        |   ₹200 |
| Mode      | Most frequent value |   ₹200 |



# 3. Minimum, Maximum, and Range

These measures help analysts understand the smallest value, largest value, and overall spread of a dataset.

# 3.1 Minimum

The minimum is the smallest value in a dataset.

*Result:* ₹100

*Excel Formula:*

excel
=MIN(B2:B6)


# 3.2 Maximum

The maximum is the largest value in a dataset.

*Result:* ₹700

*Excel Formula:*

excel
=MAX(B2:B6)


# 3.3 Range

The range measures the difference between the maximum and minimum values.

*Formula:*

Range = Maximum − Minimum

*Calculation:*

Range = 700 − 100

*Range = ₹600*

*Excel Formula:*

excel
=MAX(B2:B6)-MIN(B2:B6)


*Business Application:*

A company can use the range to understand the difference between its highest and lowest daily sales.

However, the range only considers two observations. Additional measures may be required to understand the full variability of the data.



# 4. Introduction to Exploratory Data Analysis (EDA)

Exploratory Data Analysis (EDA) is the process of examining and summarizing a dataset to understand its structure, identify patterns, detect potential problems, and develop useful questions.

EDA is usually performed before creating a final report or building a statistical or machine learning model.

# Why Is EDA Important?

EDA helps analysts:

* Understand the structure of a dataset.
* Identify missing values and duplicate records.
* Detect unusual or invalid values.
* Calculate summary statistics.
* Discover trends and patterns.
* Compare different categories.
* Identify questions that require further investigation.

# Basic EDA Workflow

1. *Understand the dataset:* Identify the number of rows, columns, and the meaning of each field.
2. *Inspect data types:* Determine whether columns contain categories, identifiers, counts, or measurements.
3. *Check data quality:* Look for missing values, duplicate records, and inconsistent entries.
4. *Calculate summary statistics:* Calculate totals, averages, medians, minimums, and maximums where appropriate.
5. *Explore patterns:* Compare categories and look for trends, unusual values, and differences.
6. *Communicate findings:* Explain what the data supports and identify limitations.

# Example EDA Questions for Sales Data

* What is the total revenue?
* What is the average revenue per order?
* Which product generates the most revenue?
* Which product has the highest quantity sold?
* Are there any unusually large transactions?
* Are any order records missing or duplicated?
* How does sales performance change over time?

These questions help transform raw data into meaningful business analysis.


# 5. Understanding Outliers

An outlier is an observation that is unusually far from the other observations in a dataset.

# Example

Consider the following values:

100, 110, 105, 115, 1000

The value 1000 is much higher than the other values and may be an outlier.

# Possible Reasons for Outliers

* A genuine unusually large transaction.
* A data-entry error.
* A measurement error.
* A special business event.
* A different population or type of transaction.

# How Should an Analyst Handle Outliers?

1. Identify the unusual value.
2. Check the original source or related records.
3. Determine whether the value is valid.
4. Understand how it affects the analysis.
5. Decide whether to retain, correct, exclude, or analyze it separately based on evidence and business requirements.
6. Document the decision.

*Important:* Never delete an outlier automatically. An unusual value may represent an important business event rather than an error.


# 6. Practical Excel Analysis

Excel provides built-in formulas that help analysts summarize datasets quickly.

# Sample Sales Dataset

| Order ID | Product  | Quantity | Revenue (₹) |
| -------- | -------- | -------: | ----------: |
| 101      | Laptop   |        2 |       80000 |
| 102      | Mouse    |        5 |        2500 |
| 103      | Keyboard |        3 |        4500 |
| 104      | Monitor  |        1 |       15000 |
| 105      | Mouse    |        2 |        1000 |

Assume the data is stored in cells A1:D6, with column headers in row 1.

# 6.1 Calculate Total Revenue

excel
=SUM(D2:D6)


*Result: ₹1,03,000*

This formula adds the revenue from all five orders.

# 6.2 Calculate Average Order Revenue

excel
=AVERAGE(D2:D6)

*Result: ₹20,600*

Average order revenue = Total Revenue / Number of Orders

= ₹1,03,000 / 5

= ₹20,600

# 6.3 Find the Highest-Value Order

excel
=MAX(D2:D6)


*Result: ₹80,000*

The laptop order generated the highest revenue.

# 6.4 Find the Lowest-Value Order

excel
=MIN(D2:D6)


*Result: ₹1,000*

The smallest revenue came from one of the mouse orders.

# 6.5 Calculate Total Quantity Sold

excel
=SUM(C2:C6)


*Result: 13 units*

This formula calculates the total number of units sold across all orders.

# 6.6 Calculate Revenue Contribution

Revenue contribution measures the percentage of total revenue generated by a particular order.

*Formula:*

Revenue Contribution = (Order Revenue / Total Revenue) × 100

For the laptop order:

Revenue Contribution = (80,000 / 1,03,000) × 100

*Result: Approximately 77.67%*

If the total revenue is calculated in cell D7, use:

excel
=D2/$D$7

Format the cell as a percentage and copy the formula down.

The dollar signs in `$D$7` create an absolute reference, so the total revenue cell remains fixed when the formula is copied.

# Important Business Observation

The laptop order contributes approximately 77.67% of total revenue in this sample.

This is a useful observation, but five orders are not enough to establish a general sales trend. An analyst should investigate additional data before drawing broader conclusions.



# 7. Revenue and Quantity Are Different Metrics

Revenue and quantity measure different aspects of business performance.

* *Quantity:* Number of units sold.
* *Revenue:* Money generated from sales.

A business may sell many low-priced items but generate more revenue from a smaller number of expensive items.

For example, five mouse units generate ₹2,500, while two laptop units generate ₹80,000 in the sample dataset.

Therefore, analysts should examine both metrics instead of assuming that the product with the highest quantity also generates the highest revenue.

# 8. Practical Exercises

# Exercise 1: Descriptive Statistics

Enter these values in Excel cells B2:B6:

100, 200, 200, 300, 700

Complete the following tasks:

1. Calculate the mean using `AVERAGE()`.
2. Calculate the median using `MEDIAN()`.
3. Calculate the mode using `MODE.SNGL()`.
4. Find the minimum using `MIN()`.
5. Find the maximum using `MAX()`.
6. Calculate the range using `MAX()-MIN()`.

### Exercise 2: Sales Data Analysis

Using the sample sales dataset:

1. Calculate total revenue.
2. Calculate average order revenue.
3. Identify the highest-value order.
4. Identify the lowest-value order.
5. Calculate total quantity sold.
6. Calculate the revenue contribution of each order.
7. Write three observations about the data.
8. Mention one limitation of your analysis.

# Exercise 3: Analytical Thinking

Suppose a company's average daily sales increased from ₹5,000 to ₹8,000.

Does this automatically mean that business performance improved?

Investigate the following questions:

* Did total revenue increase over comparable periods?
* Was the increase caused by one unusually large order?
* Did the number of orders increase or decrease?
* Did profit also increase?
* Were the periods being compared equal in length?

**Learning:** A statistic describes a pattern, but business context and additional evidence are needed to interpret it correctly.


# 9. Key Takeaways

* Data types help analysts select appropriate analysis methods.
* Categorical data represents labels and groups.
* Discrete data represents countable quantities.
* Continuous data represents measurable quantities.
* Mean represents the arithmetic average.
* Median represents the middle value.
* Mode represents the most frequently occurring value.
* Minimum and maximum identify the smallest and largest observations.
* Range measures the difference between the maximum and minimum.
* EDA helps analysts understand datasets before drawing conclusions.
* Outliers should be investigated rather than removed automatically.
* Excel formulas can summarize data efficiently.
* Revenue and quantity represent different business metrics.
* Analytical conclusions should be supported by evidence and appropriate context.

# 10. Day 4 Completion Checklist

* [ ] Learned categorical and numerical data types.
* [ ] Understood discrete and continuous data.
* [ ] Practiced mean, median, and mode.
* [ ] Calculated minimum, maximum, and range.
* [ ] Understood the purpose of EDA.
* [ ] Learned how to identify and investigate outliers.
* [ ] Practiced Excel formulas on sample sales data.
* [ ] Calculated revenue contribution.
* [ ] Completed the practical exercises.
* [ ] Documented the learning in GitHub.

# Tools Used

* Microsoft Excel
* Markdown
* Git and GitHub

