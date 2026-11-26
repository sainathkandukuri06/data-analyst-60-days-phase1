# Day 48 - Advanced Excel: Power Query for Data Cleaning and Transformation

## 📌 Overview

Today, I learned about **Power Query** in Microsoft Excel. Power Query is an important tool for Data Analysts because it helps import, clean, transform, and combine data from different sources.

In real-world projects, raw datasets often contain duplicate records, missing values, incorrect data types, unnecessary columns, and inconsistent formats.

Power Query helps solve these problems by providing a step-by-step data-cleaning process that can be repeated whenever new data arrives.

## 1. What is Power Query?

Power Query is a data connection and transformation tool available in Microsoft Excel and Power BI.

It is used to:
- Import data from different sources.
- Remove duplicate records.
- Handle missing and incorrect values.
- Change column data types.
- Split and merge columns.
- Combine multiple tables.
- Prepare clean data for analysis.

**Example:**

Suppose a company has 10,000 employee records. Some records contain duplicate employee details, blank salaries, and inconsistent city names.

Instead of cleaning every record manually, we can use Power Query to automate the cleaning process.

## 2. How to Open Power Query in Excel

Steps:

1. Open Microsoft Excel.
2. Select your dataset.
3. Go to the Data tab.
4. Click From Table/Range.
5. Power Query Editor will open.
6. Perform the required cleaning and transformation operations.

Power Query can also import data from external sources using the Get Data option.

## 3. Important Power Query Operations

### A. Remove Duplicates

Duplicate records are repeated entries in a dataset.

Power Query provides the Remove Duplicates option to eliminate repeated values based on selected columns.

**Example:**

| Employee ID | Name |
|---|---|
| 101 | Ravi |
| 102 | Suresh |
| 101 | Ravi |

After removing duplicates:

| Employee ID | Name |
|---|---|
| 101 | Ravi |
| 102 | Suresh |

**Purpose:** Prevents repeated records from affecting analysis and calculations.

### B. Remove Empty Rows

Sometimes datasets contain completely blank rows.

Power Query provides the Remove Blank Rows option to remove unnecessary empty records.

**Purpose:** Keeps the dataset clean and organized.

### C. Replace Values

Replace Values is used to replace incorrect, missing, or inconsistent values with appropriate values.

**Example:**

Before cleaning:

| Employee | City |
|---|---|
| Ravi | hyderabad |
| Suresh | N/A |
| Priya | Hyderabad |

After cleaning:

| Employee | City |
|---|---|
| Ravi | Hyderabad |
| Suresh | Unknown |
| Priya | Hyderabad |

**Purpose:** Maintains consistency across the dataset.

### D. Change Data Types

Every column should have the correct data type.

| Data Type | Example |
|---|---|
| Text | Sainath |
| Whole Number | 25000 |
| Decimal Number | 25000.50 |
| Date | 26-11-2026 |
| True/False | TRUE |

**Purpose:**
- Prevents calculation errors.
- Makes numerical analysis easier.
- Helps Power Query interpret data correctly.

### E. Split Columns

Split Columns divides one column into multiple columns based on a delimiter or position.

**Example:**

Before splitting:

| Full Name |
|---|
| Ravi Kumar |
| Suresh Reddy |

After splitting:

| First Name | Last Name |
|---|---|
| Ravi | Kumar |
| Suresh | Reddy |

**Purpose:** Separates combined information into individual columns.

### F. Merge Columns

Merge Columns combines two or more columns into a single column.

**Example:**

Before merging:

| First Name | Last Name |
|---|---|
| Ravi | Kumar |
| Suresh