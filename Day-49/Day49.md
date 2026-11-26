# Day 49 - Introduction to Data Cleaning

Today, I learned about **Data Cleaning**, one of the most important processes in Data Analytics.

Data Cleaning is the process of identifying and correcting errors, missing values, duplicate records, inconsistent information, and incorrect data formats in a dataset.

The main objective is to convert raw and messy data into clean, accurate, consistent, and reliable data for analysis.

# 1. What is Data Cleaning?

Data Cleaning is the process of improving data quality by finding and fixing errors in a dataset.

**Example:**

Before Data Cleaning:

| Employee | Age | Department | Salary |
|---|---:|---|---:|
| Rahul | 25 | IT | 30000 |
| Priya | 28 | HR | 35000 |
| Rahul | 25 | IT | 30000 |
| Arjun | Missing | it | 40000 |

Problems identified:
- Duplicate employee records.
- Missing age values.
- Inconsistent department names.
- Incorrect or incomplete information.

After Data Cleaning, the dataset becomes more consistent and suitable for analysis.

## 2. Importance of Data Cleaning

Data Cleaning is important because:

- **Accuracy:** Helps maintain correct information.
- **Consistency:** Ensures data follows a standard format.
- **Reliability:** Improves the quality of analytical results.
- **Better Decision-Making:** Helps businesses make informed decisions.
- **Better Visualization:** Prevents incorrect information in dashboards and reports.
- **Improved Analysis:** Makes datasets easier to understand and analyze.

**Important Concept:**

GIGO (Garbage In, Garbage Out) means that incorrect input data can produce incorrect output results.

## 3. Common Data Quality Problems

### A. Missing Values

Missing values occur when some information is not available in a dataset.

Example:
- Employee name is available, but age is missing.
- Product name is available, but price is missing.

**Methods to Handle Missing Values:**
- Remove records when justified.
- Replace values using Mean.
- Replace values using Median.
- Replace categorical values using Mode.
- Retrieve the correct information from the original source.

### B. Duplicate Records

Duplicate records occur when the same information appears multiple times.

Example:

| Order ID | Customer | Amount |
|---|---|---:|
| 101 | Rahul | 500 |
| 102 | Priya | 700 |
| 101 | Rahul | 500 |

Order ID 101 appears twice.

**Solution:** Identify unwanted duplicate records and remove them after checking whether they represent genuine transactions.

### C. Inconsistent Data

Inconsistent data means the same information is represented in different formats.

Example:
- IT
- it
- Information Technology
- IT Department

**Solution:** Standardize all values into a consistent format.

### D. Incorrect Data Types

Incorrect data types occur when values are stored in an unsuitable format.

Example:

| Name | Age |
|---|---|
| Rahul | 25 |
| Priya | Twenty Eight |
| Arjun | 30 |

**Solution:** Convert values into appropriate data types after validating the information.

Common data types:
- Integer
- Decimal
- Text
- Date
- Boolean

### E. Outliers

An outlier is a value that is significantly different from other values in a dataset.

Example:

Employee Salaries:

25000, 28000, 30000, 32000, 35000, 500000

Here, 500000 is an unusual value compared to the other salaries.

**Solution:** Investigate unusual values before deciding whether to correct, retain, or remove them.

An outlier is not always an error.

## 4. Data Cleaning Process

A Data Analyst generally follows these steps:

1. **Collect Data:** Obtain data from Excel, SQL databases, CSV files, or other sources.
2. **Inspect Data:** Understand the dataset, columns, rows, and data types.
3. **Identify Errors:** Find missing values, duplicates, and inconsistent information.
4. **Clean Data:** Correct errors and standardize the dataset.
5. **Validate Data:** Verify that the cleaned data is accurate and consistent.
6. **Save Clean Data:** Store the cleaned dataset for further analysis.

## 5. Tools Used for Data Cleaning

| Tool | Purpose |
|---|---|
| Microsoft Excel | Remove duplicates, handle missing values, sort and filter data |
| Power Query | Import, transform, and clean datasets |
| Python (Pandas) | Automate data cleaning and manipulation |
| SQL | Identify missing values, duplicates, and incorrect records |

## 6. Practical Example

Consider an e-commerce company's sales dataset.

| Order ID | Customer | Product | Amount |
|---|---|---|---:|
| 101 | Rahul | Laptop | 50000 |
| 102 | Priya | Mobile | 20000 |
| 101 | Rahul | Laptop | 50000 |
| 103 | Arjun | Headphones | Blank |
| 104 | Sneha | Tablet | -1000 |

Problems to identify:

- Duplicate order IDs.
- Missing sales amounts.
- Negative sales amounts.
- Incorrect or inconsistent information.

As a Data Analyst, I should investigate these problems and clean the dataset before calculating total sales or creating reports.

## 7. Key Learnings

Today, I learned:

- Introduction to Data Cleaning.
- Importance of data quality.
- Identifying missing values.
- Identifying duplicate records.
- Understanding inconsistent data.
- Identifying incorrect data types.
- Understanding outliers.
- Learning the basic data cleaning workflow.
- Understanding tools used for data cleaning.

## 8. Interview Questions

1. What is Data Cleaning?
2. Why is Data Cleaning important in Data Analytics?
3. What are duplicate records?
4. How do you handle missing values?
5. What is an outlier?
6. What is the difference between data cleaning and data transformation?
7. Which tools are commonly used for data cleaning?
8. What does GIGO mean?

