# Day 2 - Data Analyst Challenge: Data Fundamentals

#  Learning Objectives

* Understand business problems and data problems.
* Learn different types of data.
* Understand rows, columns, records, attributes, and cells.
* Differentiate dimensions and measures.
* Understand metrics and Key Performance Indicators (KPIs).
* Learn aggregation functions.
* Understand data granularity.
* Learn how to convert business problems into analytical questions.

# Concepts Learned

# 1. Business Problems vs. Data Problems

*Business Problem:* A challenge that affects an organization's goals, revenue, costs, or performance.

Examples:

* Decreasing sales revenue.
* Increasing customer complaints.
* High delivery costs.
* Low customer retention.

*Data Problem:* A question that can be investigated using data to understand a business problem.

Examples:

* Why did sales decrease?
* Which region generated the lowest revenue?
* Which products have declining sales?
* What percentage of customers make repeat purchases?

# 2. Types of Data

*Structured Data*

* Organized in rows and columns.
* Examples: Excel spreadsheets, SQL tables, and CSV files.

*Semi-Structured Data*

* Contains organizational elements but does not always follow a fixed tabular structure.
* Examples: JSON files, XML documents, and application logs.

*Unstructured Data*

* Does not naturally follow a fixed rows-and-columns structure.
* Examples: images, audio recordings, videos, and customer reviews.

Quantitative Data: Numerical quantities such as revenue, salary, age, and quantity sold.

Qualitative Data: Descriptive or categorical information such as product category, region, and payment method.

Discrete Data: Countable values, such as the number of orders.

Continuous Data: Measurable values, such as delivery time and distance.

# 3. Rows, Columns, Records, Attributes, and Cells

* Row: Represents one record or observation.
* Column: Represents a field or characteristic.
* Record: A complete set of field values for one observation.
* Attribute: A characteristic represented by a field.
* Cell: The intersection of a row and a column.

These concepts are essential when working with Excel, SQL databases, and Power BI.

# 4. Dimensions vs. Measures

*Dimensions:* Describe or categorize data.

Examples:

* Product
* Region
* Customer
* Department
* Date

*Measures:* Numerical values or calculations used to evaluate performance.

Examples:

* Total Revenue
* Total Profit
* Number of Orders
* Units Sold
* Average Order Value

Dimensions help answer *by what category?*, while measures help answer *what should be calculated?*

# 5. Metrics vs. KPIs

*Metric:* A measurable value that describes business activity or performance.

Examples:

* Total Sales
* Website Visitors
* Number of Orders
* Average Delivery Time

*KPI (Key Performance Indicator):* A measure selected to evaluate progress toward an important business objective.

Examples:

* Monthly Revenue Growth
* Customer Retention Rate
* Customer Acquisition Cost
* On-Time Delivery Rate

A metric becomes a KPI when it is important for measuring progress toward a defined business goal.

# 6. Aggregation Functions

Aggregation combines multiple values into a summarized result.

| Function       | Purpose                        |
| -------------- | ------------------------------ |
| SUM            | Calculates the total           |
| COUNT          | Counts records or values       |
| AVERAGE        | Calculates the arithmetic mean |
| MIN            | Finds the smallest value       |
| MAX            | Finds the largest value        |
| COUNT DISTINCT | Counts unique values           |

These functions are commonly used in Excel, SQL, and Power BI.

# 7. Data Granularity

Granularity refers to the level of detail represented by a dataset.

Examples:

* Order-line level: One row per product line within an order.
* Order level: One row per order.
* Daily level: One row per day.
* Monthly level: One row per month.

Understanding granularity prevents incorrect calculations, such as counting order lines instead of unique orders.

# 8. Analytical Thinking

A Data Analyst should understand the business problem before performing calculations or creating visualizations.

Five important questions to ask:

1. What happened?
2. When did it happen?
3. Where did it happen?
4. Who or what contributed to the result?
5. What action should the business consider?

Analytical questions help identify patterns, investigate business performance, and support evidence-based decisions.

# Practical Assignment: Sales Analysis

I practiced analytical thinking using the following sample sales dataset.

| Order ID | Region    | Product  | Quantity | Revenue |
| -------- | --------- | -------- | -------: | ------: |
| 101      | Hyderabad | Laptop   |        1 |   50000 |
| 102      | Chennai   | Mouse    |        2 |    1000 |
| 103      | Hyderabad | Keyboard |        1 |    2000 |
| 104      | Chennai   | Laptop   |        1 |   45000 |
| 105      | Hyderabad | Mouse    |        3 |    1500 |

# Analysis Tasks

* Identify the number of rows and columns.
* Classify dimensions and measures.
* Calculate total revenue.
* Calculate total quantity sold.
* Calculate the number of orders.
* Calculate average revenue per order.
* Compare revenue by region.
* Identify useful business questions from the dataset.

# Expected Results

| Metric                    | Result |
| ------------------------- | -----: |
| Total Records             |      5 |
| Total Revenue             |  99500 |
| Total Quantity Sold       |      8 |
| Number of Orders          |     5* |
| Average Revenue per Order |  19900 |
| Hyderabad Revenue         |  53500 |
| Chennai Revenue           |  46000 |

*Assumption: Each row represents one unique order.*

# Key Takeaways

* Business problems define what needs to be investigated.
* Data analysis helps answer business questions using evidence.
* Data can be classified by its structure and meaning.
* Dimensions categorize data, while measures quantify results.
* KPIs measure progress toward important business objectives.
* Aggregation summarizes data into meaningful results.
* Granularity must be understood before calculating metrics.
* Good analytical questions lead to better business insights.


#  Sample Sales Data Analysis Dataset

# Description

This Excel workbook contains a sample sales dataset created for practicing fundamental Data Analytics concepts as part of my *60-Day Data Analyst Challenge – Phase 1*.

The dataset contains 30 fictional sales records and 13 columns, including order details, order dates, regions, products, categories, quantities, unit prices, costs, revenue, profit, sales channels, and order statuses.

#  Worksheets Included

* *Sales_Data:* Contains the sample sales records for data exploration and analysis.
* *Data_Dictionary:* Explains the meaning and classification of each column, including dimensions and measures.
* *Practice_Tasks:* Contains 10 practical exercises to strengthen analytical thinking and data interpretation skills.

#  Learning Objectives

* Understand structured data, rows, columns, records, and attributes.
* Identify dimensions and measures in a sales dataset.
* Calculate total revenue, cost, profit, and quantity sold.
* Practice aggregation functions such as SUM, COUNT, and AVERAGE.
* Compare sales performance across regions and product categories.
* Understand data granularity and the importance of accurate calculations.
* Develop business questions and generate meaningful insights from data.

#  Tools Used

* Microsoft Excel
* Git and GitHub

# Purpose of the Project

The purpose of this dataset is to build a strong foundation in data analysis before progressing to advanced concepts such as SQL, Python, Power BI, data modeling, and dashboard development.




