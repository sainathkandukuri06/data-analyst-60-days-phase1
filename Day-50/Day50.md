# Day 50 - Data Cleaning: Handling Missing Values, Duplicates & Inconsistent Data

Data cleaning helps transform raw and unorganized data into accurate, consistent, and reliable information for analysis.

## 1. What is Data Cleaning?

Data Cleaning is the process of identifying and correcting errors, inconsistencies, missing values, and duplicate records in a dataset.

**Example:**

Consider the following employee dataset:

| Employee ID | Name | City | Salary |
|---|---|---|---:|
| 101 | Ravi | Hyderabad | 25000 |
| 102 | Suresh | hyderabad | 30000 |
| 103 | Priya | Chennai | |
| 101 | Ravi | Hyderabad | 25000 |
| 104 | Kumar | Mumbai | 35000 |

Problems:
- Duplicate employee records.
- Missing salary values.
- Inconsistent city names.
- Data quality issues.

A Data Analyst must identify and correct these problems before performing analysis.

## 2. Handling Missing Values

Missing values occur when information is unavailable or not entered in a dataset.

**Example:**

| Employee | Salary |
|---|---:|
| Ravi | 25000 |
| Suresh | |
| Priya | 30000 |

Suresh's salary is missing.

### Methods to Handle Missing Values

**A. Remove Missing Records**

Remove rows containing missing values when those records are unnecessary and removal is appropriate.

**B. Replace with Mean**

Mean is the average of numerical values.

Formula:

Mean = Sum of Values / Number of Values

Example:

Salaries: 20000, 30000, 40000

Mean = (20000 + 30000 + 40000) / 3

Mean = 30000

A missing salary can be replaced with 30000 when mean imputation is appropriate.

**C. Replace with Median**

Median is the middle value after arranging numbers in ascending order.

Example:

Values: 10000, 20000, 30000

Median = 20000

Median is often useful when numerical data contains extreme values.

**D. Replace with Mode**

Mode is the most frequently occurring value.

Example:

Cities: Hyderabad, Chennai, Hyderabad, Mumbai, Hyderabad

Mode = Hyderabad

Mode can be used to fill missing categorical values when appropriate.

**Important:** Never replace missing values blindly. Understand the business meaning of the missing information first.

## 3. Handling Duplicate Records

Duplicate records are repeated entries in a dataset.

**Example:**

Before cleaning:

| ID | Name | City |
|---|---|---|
| 101 | Ravi | Hyderabad |
| 102 | Suresh | Chennai |
| 101 | Ravi | Hyderabad |

After removing duplicates:

| ID | Name | City |
|---|---|---|
| 101 | Ravi | Hyderabad |
| 102 | Suresh | Chennai |

### Why Remove