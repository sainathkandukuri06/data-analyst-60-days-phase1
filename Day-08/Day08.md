# Day 08: Data Cleaning and Data Transformation

# Learning Objectives

- Understand data cleaning and data transformation.
- Identify and handle missing values.
- Detect and remove duplicate records appropriately.
- Standardize inconsistent text values.
- Understand data types and data formatting.
- Calculate revenue using Excel formulas.
- Learn how Power Query supports repeatable data preparation.
- Understand data validation and data quality rules.
- Prepare a dataset for reporting and dashboard development.

---

## 1. Data Cleaning

# Definition

Data cleaning is the process of identifying and correcting inaccurate, incomplete, duplicated, inconsistent, or invalid data.

# Common Data Quality Problems

| Problem | Description | Example |
|---|---|---|
| Missing values | Required information is absent | Quantity is blank |
| Duplicate records | A record is unintentionally repeated | Same transaction recorded twice |
| Inconsistent text | Different formats represent the same category | Hyderabad, hyderabad |
| Incorrect data types | Values are stored in an unsuitable format | Date stored as text |
| Invalid values | Values violate business rules | Negative sales quantity |
| Extra spaces | Unnecessary spaces appear in text | " Hyderabad " |

# Why Is Data Cleaning Important?

- Improves data accuracy and consistency.
- Prevents incorrect calculations.
- Reduces errors in reports and dashboards.
- Improves the reliability of business decisions.
- Makes data easier to analyze using Excel, SQL, Python, and Power BI.


# 2. Handling Missing Values

A missing value occurs when a field does not contain the expected information.

# Example

| Employee | Department | Salary |
|---|---|---:|
| Ravi | IT | 40000 |
| Priya | HR | |
| Arun | IT | 50000 |

Priya's salary is missing.

# Methods for Handling Missing Values

1. **Investigate the source:** Recover the missing value from the original system when possible.
2. **Replace the value:** Use an appropriate method, such as a justified median or other estimate, when suitable.
3. **Exclude the record:** Remove it from a particular analysis only when justified and after considering the impact.
4. **Leave it missing:** Retain the blank when the correct value is unknown and replacement would be misleading.

*Important:** A blank value is not necessarily equal to zero. Always understand the business meaning before replacing missing data.

# Excel Formulas

Count numeric entries:

```excel
=COUNT(C2:C10)
```

Count blank cells:

```excel
=COUNTBLANK(C2:C10)
```

---

## 3. Identifying Duplicate Records

A duplicate record occurs when the same real-world event or entity is recorded more than once.

### Example

| Order ID | Product | Revenue |
|---|---|---:|
| 101 | Laptop | 100000 |
| 102 | Mouse | 1500 |
| 102 | Mouse | 1500 |

If the second record is an accidental duplicate, it can overstate the total revenue by ₹1,500.

### How to Handle Duplicates in Excel

1. Select the dataset.
2. Open the **Data** tab.
3. Select **Remove Duplicates**.
4. Choose the columns that define a unique record.
5. Review the result and verify the record count.

**Important:** Do not delete records simply because their values look similar. Confirm whether they represent the same transaction. For example, one order may contain multiple products.

---

## 4. Standardizing Inconsistent Text

Text standardization ensures that the same category is represented consistently throughout the dataset.

### Example

| Original Value | Standardized Value |
|---|---|
| Hyderabad | Hyderabad |
| hyderabad | Hyderabad |
| HYDERABAD | Hyderabad |
|  Hyderabad  | Hyderabad |

Inconsistent city names can cause a reporting tool to treat the same city as separate categories.

### Useful Excel Functions

**TRIM:** Removes unnecessary spaces.

```excel
=TRIM(A2)
```

**PROPER:** Converts text to title case.

```excel
=PROPER(A2)
```

**CLEAN:** Removes certain non-printing characters.

```excel
=CLEAN(A2)
```

**Combined formula:**

```excel
=PROPER(TRIM(CLEAN(A2)))
```

These functions improve formatting, but they cannot determine whether different names or abbreviations represent the same real-world category. That requires business knowledge or reference data.

---

## 5. Understanding Data Types

A data type defines how a value should be interpreted and processed.

| Column | Suitable Data Type | Example |
|---|---|---|
| Order ID | Text or whole number, depending on requirements | 00125 |
| Quantity | Whole number | 4 |
| Unit Price | Decimal or currency | 799.50 |
| Order Date | Date | 2026-10-15 |
| Revenue | Decimal or currency | 3198.00 |
| City | Text | Hyderabad |

### Why Data Types Matter

- Incorrect data types can cause calculation errors.
- Dates stored as text may not sort or filter correctly.
- Numeric IDs may lose leading zeros.
- Text-formatted numbers may not work properly in calculations.
- Correct data types improve analysis and reporting.

**Key lesson:** Applying a display format does not always correct the underlying data type.

---

## 6. Data Transformation

### Definition

Data transformation is the process of changing the structure, format, or representation of data so that it is suitable for analysis.

### Common Transformation Operations

- Combining columns.
- Splitting columns.
- Changing data types.
- Standardizing date formats.
- Creating calculated columns.
- Grouping dates by month or year.
- Reshaping tables.
- Merging datasets.

### Example: Combining Names

| First Name | Last Name | Full Name |
|---|---|---|
| Ravi | Kumar | Ravi Kumar |
| Priya | Sharma | Priya Sharma |

Excel formula:

```excel
=A2&" "&B2
```

### Cleaning vs. Transformation

| Data Cleaning | Data Transformation |
|---|---|
| Fixes data quality problems | Changes data representation or structure |
| Handles missing values | Combines columns |
| Removes confirmed duplicates | Splits columns |
| Standardizes inconsistent values | Changes data types |
| Improves data quality | Prepares data for analysis |

Some operations, such as standardizing city names, can serve both purposes.

---

## 7. Revenue Calculation in Excel

Revenue is the amount generated from selling products or services before accounting for other financial factors, depending on the business definition.

### Formula

**Revenue = Quantity × Unit Price**

### Example

| Product | Quantity | Unit Price | Revenue |
|---|---:|---:|---:|
| Laptop | 1 | ₹50000 | ₹50000 |
| Mouse | 2 | ₹500 | ₹1000 |
| Keyboard | 3 | ₹1500 | ₹4500 |

Excel formula, assuming Quantity is in `C2` and Unit Price is in `D2`:

```excel
=C2*D2
```

To calculate total revenue from valid records, sum the Revenue column:

```excel
=SUM(E2:E10)
```

Before calculating revenue, confirm that the required inputs are valid and that the business rules are satisfied.

---

## 8. Data Cleaning Using Power Query

### What Is Power Query?

Power Query is a data preparation and transformation tool available in Microsoft Excel and Power BI.

It allows analysts to import, clean, transform, combine, and prepare data through a sequence of repeatable steps.

### Typical Workflow

1. Import data from Excel, CSV, databases, or other supported sources.
2. Inspect the column names and data types.
3. Identify missing values and duplicate records.
4. Standardize text and date formats.
5. Filter or transform records according to business rules.
6. Load the prepared data into Excel or the Power BI data model.
7. Refresh the query when new source data becomes available.

### Opening Power Query in Excel

1. Open Excel.
2. Select your data.
3. Choose **Data → From Table/Range**.
4. Make the required transformations in Power Query Editor.
5. Select **Close & Load**.

### Opening Power Query in Power BI

1. Open Power BI Desktop.
2. Select **Home → Transform data**.
3. Perform the required cleaning and transformation steps.
4. Select **Close & Apply**.

### Benefits of Power Query

- Reduces repetitive manual work.
- Saves transformation steps.
- Helps standardize recurring data preparation.
- Supports data from multiple sources.
- Makes refresh-based workflows easier to maintain.

Power Query stores transformation instructions, commonly expressed in the M language. Refreshing a query reapplies the steps, but the output must still be checked for errors or unexpected changes.

---

## 9. Data Validation

### Definition

Data validation is the process of checking whether data satisfies defined requirements and business rules.

### Examples of Validation Rules

| Column | Validation Rule |
|---|---|
| Order ID | Must not be blank |
| Quantity | Must be a positive whole number |
| Unit Price | Must not be negative |
| Order Date | Must be a valid date |
| City | Must match an accepted category |
| Revenue | Must match Quantity × Unit Price when the inputs are valid |

### Cleaning vs. Validation

- **Cleaning:** Correcting or handling identified data problems.
- **Validation:** Checking whether the data meets the required rules.

For example, if a sales quantity is `-5`, a validation rule can flag it because sales quantities are expected to be positive.

In Excel, use **Data → Data Validation** to restrict user input according to rules such as whole numbers greater than zero.

A mathematically correct calculation does not automatically mean the source data is valid.

---

## 10. Practical Exercise: Sales Dataset Cleaning

### Sample Raw Dataset

| Order ID | Product | Quantity | Unit Price | City |
|---|---|---:|---:|---|
| 201 | Laptop | 1 | 50000 | Hyderabad |
| 202 | Mouse | 2 | 500 | hyderabad |
| 203 | Keyboard | 3 | 1500 | Chennai |
| 203 | Keyboard | 3 | 1500 | Chennai |
| 204 | Monitor | | 8000 | Bengaluru |

### Tasks Completed or Practised

- [ ] Inspect the raw dataset for quality issues.
- [ ] Identify missing values.
- [ ] Investigate whether Order ID 203 is a genuine duplicate.
- [ ] Standardize city names.
- [ ] Investigate the missing quantity for Monitor.
- [ ] Create a Revenue column using Quantity × Unit Price.
- [ ] Validate data types and business rules.
- [ ] Compare the cleaned data with the original dataset.

### Expected Revenue for Complete Records

| Product | Calculation | Revenue |
|---|---|---:|
| Laptop | 1 × 50000 | ₹50000 |
| Mouse | 2 × 500 | ₹1000 |
| Keyboard | 3 × 1500 | ₹4500 |

If the repeated Keyboard row is confirmed to be an accidental duplicate, the subtotal for the three distinct, complete orders is **₹55,500**.

The Monitor revenue remains unresolved until its missing quantity is investigated. Therefore, ₹55,500 is not necessarily the final total revenue for the entire dataset.

---

## 11. Data Quality Dimensions

Professional Data Analysts should understand the following dimensions:

| Dimension | Meaning |
|---|---|
| Accuracy | Data correctly represents reality |
| Completeness | Required information is available |
| Consistency | Data follows consistent formats and definitions |
| Validity | Values satisfy defined rules |
| Uniqueness | Records are not duplicated when uniqueness is required |
| Traceability | Data sources and transformation steps can be explained |

These dimensions help analysts assess whether a dataset is ready for reporting and business decision-making.

---

## 12. Key Learnings

By completing Day 08, I learned:

- What data cleaning means and why it is important.
- How to identify missing values and duplicate records.
- How to standardize text using Excel functions.
- Why data types matter for calculations and reporting.
- How data transformation prepares information for analysis.
- How to calculate revenue using Excel formulas.
- How Power Query supports repeatable data preparation.
- How validation rules help identify invalid data.
- Why data quality is essential for trustworthy reports and dashboards.

---

#  13. Interview Preparation Questions

1. What is data cleaning, and why is it important?
2. What is the difference between a missing value and zero?
3. How do you identify and remove duplicate records in Excel?
4. What are TRIM, PROPER, and CLEAN used for?
5. What is the difference between data cleaning and data transformation?
6. What is Power Query, and why do Data Analysts use it?
7. What is data validation?
8. How can incorrect data types affect analysis?
9. How do you calculate revenue from quantity and unit price?
10. What are the key dimensions of data quality?


