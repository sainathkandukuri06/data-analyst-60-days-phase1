# Data Analytics Foundations

#  Overview

Today focuses on understanding the fundamentals of Data Analytics, the responsibilities of a Data Analyst, the data analysis workflow, and basic Excel concepts.

The objective is to understand how raw data can be transformed into meaningful information that supports business decisions.

# Learning Objectives

* Understand the meaning of Data, Information, and Data Analytics.
* Learn the four types of Data Analytics.
* Understand the responsibilities of a Data Analyst.
* Learn the steps involved in the data analysis process.
* Understand the differences between Excel, SQL, Python, and Power BI.
* Learn basic Excel terminology and formulas.
* Perform a simple sales data analysis.
* Understand basic data quality issues.
* Document daily learning progress using GitHub.

# 1. What Is Data?

Data is a collection of facts, observations, or measurements.

*Examples:*

* Student marks
* Product prices
* Customer information
* Sales transactions
* Employee records

### Data vs Information

* Data: Raw facts and figures collected from different sources.
* Information: Meaningful results obtained by organizing and analyzing data.

For example, daily sales figures are raw data. Calculating total sales, average sales, and highest sales converts those figures into useful information.

# 2. What Is Data Analytics?

Data Analytics is the process of collecting, cleaning, transforming, and analyzing data to identify patterns, answer questions, and support business decisions.

# Real-World Example

An online shopping company wants to understand why sales are decreasing.

A Data Analyst can examine:

* Monthly sales trends
* Product performance
* Customer purchasing behavior
* Discounts and returns
* Regional sales performance

The analyst uses these findings to identify possible reasons and recommend actions supported by evidence.

# 3. Types of Data Analytics

# 1. Descriptive Analytics

Question: What happened?

Summarizes historical data.

Example: Total sales last month were ₹5,00,000.

# 2. Diagnostic Analytics

**Question:** Why did it happen?

Investigates the reasons behind a result.

Example: Sales decreased after a popular product went out of stock.

# 3. Predictive Analytics

**Question:** What might happen?

Uses historical data and analytical methods to estimate future outcomes.

Example: Forecasting next month's sales.

# 4. Prescriptive Analytics

**Question:** What should we do?

Evaluates possible actions and helps recommend decisions.

Example: Recommending stock levels based on expected demand and storage costs.

# 4. Responsibilities of a Data Analyst

A Data Analyst typically performs the following tasks:

1. Collect data from different sources.
2. Clean and validate data.
3. Analyze data using appropriate techniques.
4. Identify patterns and trends.
5. Create reports, charts, and dashboards.
6. Communicate findings to stakeholders.
7. Support business decisions using data.

# 5. Data Analysis Workflow

The typical data analysis workflow includes:

1. **Data Collection:** Obtain data from spreadsheets, databases, APIs, or other sources.
2. **Data Cleaning:** Handle missing values, duplicates, inconsistent formats, and errors.
3. **Data Analysis:** Calculate metrics, compare categories, and identify patterns.
4. **Data Visualization:** Present findings using charts, graphs, and dashboards.
5. **Communication:** Explain the findings and their business implications.
6. **Decision Support:** Help stakeholders evaluate possible actions.

These steps may repeat as new questions or data-quality issues arise.

# 6. Common Data Analyst Tools

| Tool             | Primary Purpose                                    |
| ---------------- | -------------------------------------------------- |
| Microsoft Excel  | Spreadsheet calculations and analysis              |
| SQL              | Retrieving and analyzing database data             |
| Python           | Automation and programmatic data analysis          |
| Pandas and NumPy | Data manipulation and numerical computing          |
| Power Query      | Data extraction, cleaning, and transformation      |
| Power BI         | Interactive reports and dashboards                 |
| DAX              | Calculations and measures in Power BI              |
| Statistics       | Understanding variation, relationships, and trends |

# 7. Excel Fundamentals

Excel is a spreadsheet application used to organize, calculate, analyze, and visualize data.

# Basic Terminology

| Term         | Description                            |
| ------------ | -------------------------------------- |
| Workbook     | An Excel file                          |
| Worksheet    | A sheet inside a workbook              |
| Row          | A horizontal record                    |
| Column       | A vertical field                       |
| Cell         | The intersection of a row and a column |
| Cell Address | A cell reference, such as B2           |
| Range        | A group of cells, such as D2:D6        |
| Header       | A label describing a column            |
| Record       | One entry in a dataset                 |

# Important Excel Formulas

| Formula                      | Purpose                 |
| ---------------------------- | ----------------------- |
| `=SUM(D2:D6)`                | Calculates the total    |
| `=AVERAGE(D2:D6)`            | Calculates the average  |
| `=MAX(D2:D6)`                | Finds the maximum value |
| `=MIN(D2:D6)`                | Finds the minimum value |
| `=COUNT(D2:D6)`              | Counts numeric cells    |
| `=IF(D2>10000,"High","Low")` | Evaluates a condition   |

# Sorting and Filtering

* **Sorting:** Arranges records in ascending or descending order.
* **Filtering:** Displays only records that meet specified conditions.

These features help analysts explore datasets efficiently.

# 8. Practical Exercise: Sales Data Analysis

# Dataset

| Product    | Quantity | Unit Price (₹) | Revenue (₹) |
| ---------- | -------: | -------------: | ----------: |
| Laptop     |        2 |         45,000 |      90,000 |
| Mouse      |       10 |            500 |       5,000 |
| Keyboard   |        5 |          1,200 |       6,000 |
| Monitor    |        3 |         12,000 |      36,000 |
| Headphones |        4 |          2,500 |      10,000 |

# Revenue Calculation

Revenue is calculated using:

`Revenue = Quantity × Unit Price`

In Excel, enter the following formula in cell D2:

`=B2*C2`

Copy the formula down to the remaining product rows.

# Analysis Formulas

**Total Revenue**

`=SUM(D2:D6)`

Result: ₹1,47,000

Average Revenue per Product Record

`=AVERAGE(D2:D6)`

Result: ₹29,400

Highest Revenue

`=MAX(D2:D6)`

Result: ₹90,000

Lowest Revenue

`=MIN(D2:D6)`

Result: ₹5,000

Number of Product Records

`=COUNT(D2:D6)`

Result: 5

# 9. Business Insights

Based on the sample dataset:

1. Laptop revenue is the highest: ₹90,000.
2. Mouse revenue is the lowest: ₹5,000.
3. Total revenue is ₹1,47,000** across the five product records.
4. Laptops and monitors together generate ₹1,26,000**, approximately 85.7% of total revenue.
5. The mouse has the highest quantity sold, but it does not generate the highest revenue.

These findings describe the sample dataset. Further information, such as product costs and profit margins, would be needed to assess profitability.

# 10. Introduction to Data Quality

Data quality affects the reliability of analytical results.

Common data-quality issues include:

* Missing Values: Required information is not recorded.
* Duplicates: Records are repeated according to the relevant business rules.
* Inconsistent Formats: Values are represented differently.
* Invalid Values: Data does not satisfy expected rules.

Analysts should investigate these issues before making conclusions. Missing values should not automatically be replaced with zero, and repeated records should be checked before deletion.

# 11. Key Learnings

After completing Day 1, I learned:

* The fundamentals of Data Analytics.
* The difference between raw data and information.
* The four types of Data Analytics.
* The responsibilities of a Data Analyst.
* The data analysis workflow.
* Basic Excel terminology and formulas.
* How to calculate revenue using Excel.
* How to interpret results as business insights.
* The importance of data quality.
* How to document my learning journey on GitHub.

# 12. Day 1 Deliverables

* [ ] Study Data Analytics fundamentals.
* [ ] Create the sales dataset in Excel.
* [ ] Practise basic Excel formulas.
* [ ] Calculate total and average revenue.
* [ ] Identify the highest- and lowest-revenue products.
* [ ] Write business insights.
* [ ] Save the dataset and learning notes.
* [ ] Upload the work to GitHub.

Challenge Progress: Day 1 / 60
Focus: Data Analytics Foundations and Excel Basics