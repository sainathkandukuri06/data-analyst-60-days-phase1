# Day 3: Data Quality, Data Profiling & Data Validation


# Learning Objectives

* Understand the importance of data quality.
* Learn the six dimensions of data quality.
* Understand data profiling and its purpose.
* Learn data validation and business rules.
* Identify missing values, duplicate records, inconsistent formats, invalid values, and outliers.
* Understand the difference between data profiling, data validation, and data cleaning.
* Perform a basic data quality audit on a sales dataset.

#  Concepts Learned

# 1. Data Quality

Data quality describes how suitable, accurate, complete, and reliable data is for its intended purpose.

*Six dimensions of data quality:*

1. *Accuracy:* Data correctly represents real-world information.
2. *Completeness:* Required values are present.
3. *Consistency:* Data follows consistent rules and formats.
4. *Uniqueness:* Records that should be unique are not unintentionally duplicated.
5. *Timeliness:* Data is sufficiently up to date for its intended use.
6. *Validity:* Data follows predefined rules, formats, and acceptable ranges.

# 2. Data Profiling

Data profiling is the process of examining a dataset to understand its structure, distributions, patterns, and potential quality issues.

Common profiling activities include:

* Checking the number of rows and columns.
* Identifying missing values.
* Checking data types.
* Identifying potential duplicate records.
* Examining minimum, maximum, and average values.
* Analyzing the frequency of categorical values.

# 3. Data Validation

Data validation checks whether data follows predefined rules and conditions.

*Examples:*

* Order IDs must not be blank.
* Quantity must be positive for normal sales records.
* Unit price must not be negative.
* Order dates must contain valid date values.
* Transaction IDs must be unique when required by the table design.
* Revenue must match the defined business calculation.

# 4. Common Data Quality Issues

| Issue                | Description                            | Example                             |
| -------------------- | -------------------------------------- | ----------------------------------- |
| Missing Values       | Required information is absent         | Missing quantity                    |
| Duplicate Records    | The same record appears more than once | Repeated transaction                |
| Inconsistent Formats | Values use different formats           | Hyderabad, hyderabad                |
| Invalid Values       | Values violate defined rules           | Negative quantity for a normal sale |
| Outliers             | Observations are unusually extreme     | Unusually high sales                |
| Incorrect Data Types | Values use an unsuitable data type     | Revenue stored as text              |

# 5. Data Profiling vs. Data Cleaning vs. Data Validation

| Concept         | Purpose                                       |
| --------------- | --------------------------------------------- |
| Data Profiling  | Examines data and identifies potential issues |
| Data Validation | Checks data against defined rules             |
| Data Cleaning   | Corrects or manages identified data problems  |

# Practical Exercise: Sales Data Quality Audit

I practiced identifying data quality issues in a sample sales dataset containing the following fields:

* Order ID
* Product
* Quantity
* Unit Price
* Revenue

# Issues Identified

1. Missing quantity values.
2. Potentially duplicated order records.
3. Negative quantities that violate the assumed normal-sales rules.
4. Revenue values that cannot be verified because required information is missing.
5. The need to verify records before calculating reliable sales totals.

# Business Rules Applied

* Quantity must be greater than zero for normal sales records.
* Revenue should equal Quantity × Unit Price under the assumed revenue definition.
* Potential duplicates must be investigated before removal.
* Missing values must not automatically be replaced with zero.
* Unusual values must be investigated before correction.

# Key Finding

Data quality checks are essential before calculating business metrics or building dashboards. Incorrect or incomplete data can lead to misleading reports and poor business decisions.

# Key Learnings

* Reliable data is essential for accurate analysis.
* Missing values and zero values are not the same.
* Duplicate records should be investigated before deletion.
* Outliers are not always errors.
* Data profiling helps discover potential data issues.
* Data validation ensures compliance with business rules.
* Data cleaning improves data quality.
* Data quality should be checked before creating reports and dashboards.

# Interview Preparation

1. What is data quality?
2. What are the six dimensions of data quality?
3. What is data profiling?
4. What is the difference between data profiling and data cleaning?
5. What is data validation?
6. How do you identify duplicate records?
7. Why should missing values not automatically be replaced with zero?
8. What is an outlier?
9. How does poor data quality affect business decisions?
10. Why should data quality checks be performed before dashboard creation?

# Outcome

By completing Day 3, I developed a foundational understanding of data quality, data profiling, data validation, and common data quality problems.

These concepts will help me prepare datasets for reliable analysis using Excel, SQL, Python, and Power BI in upcoming challenges.



