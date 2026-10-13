# Day 05: Data Cleaning and Data Quality

## 60-Day Data Analyst Challenge — Phase 1

Welcome to Day 5 of my 60-Day Data Analyst Challenge!

Today, I learned the fundamentals of data cleaning, data quality, missing values, duplicate records, inconsistent data, invalid values, and Excel techniques for preparing reliable datasets.

Data cleaning is one of the most important responsibilities of a Data Analyst because the quality of analysis depends on the quality of the data used.

---

# Learning Objectives

By the end of Day 5, I learned:

- What data cleaning is and why it is important.
- The major dimensions of data quality.
- How to identify and handle missing values.
- How to identify duplicate records.
- How to standardize inconsistent text.
- How to identify invalid values using business rules.
- How to recognize incorrect data formats.
- How to investigate outliers.
- How to use Excel formulas for data cleaning.
- Introduction to Power Query.
- How to validate and document cleaning operations.


# 1. What Is Data Cleaning?

Data cleaning is the process of identifying and handling inaccurate, incomplete, duplicated, inconsistent, or incorrectly formatted data so that it is suitable for analysis.

Raw data can contain errors because it comes from different systems, applications, databases, spreadsheets, and user inputs.

### Example

Consider this raw sales dataset:

| Order ID | Product  |  Quantity | Revenue |
| -------- | -------- | --------: | ------: |
| 101      | Laptop   |         2 |   80000 |
| 102      | mouse    |         5 |    2500 |
| 102      | mouse    |         5 |    2500 |
| 103      | Keyboard |         3 |    4500 |
| 104      | Monitor  | *(blank)* |   15000 |

Problems identified:

- Order 102 appears twice.
- Product names have inconsistent capitalization.
- The quantity for Order 104 is missing.

These issues must be investigated before the dataset is used for reporting.

### Why Is Data Cleaning Important?

- Improves data reliability.
- Reduces errors in reports.
- Helps prevent incorrect calculations.
- Improves the quality of business decisions.
- Makes datasets easier to analyze.
- Helps prepare data for Excel, SQL, Python, and Power BI.

**Key takeaway:** Incorrect data can produce incorrect insights, even when the formulas and visualizations are correct.

---

## 2. Dimensions of Data Quality

Data quality describes how suitable data is for its intended purpose.

### 2.1 Accuracy

Accuracy means that recorded values correctly represent the real-world information.

**Example:** An invoice shows ₹2,500, but the dataset contains ₹25,000.

The value may be inaccurate and should be checked against the original source.

### 2.2 Completeness

Completeness means that required information is available.

**Example:** A sales record contains an Order ID and Product Name but has no Order Date.

The missing information may affect time-based analysis.

### 2.3 Consistency

Consistency means that the same information follows compatible formats and rules across records and systems.

**Example:**

- Hyderabad
- HYDERABAD
- hyderabad

These values may refer to the same city but use different capitalization.

### 2.4 Validity

Validity means that data follows the required format, type, and business rules.

**Example:** A Quantity column contains the text `five` instead of a numeric value.

The value needs investigation before numerical analysis.

### 2.5 Uniqueness

Uniqueness means that records that should be unique do not contain unintended duplicates.

**Example:** The same transaction is imported twice and counted twice in the revenue report.

| Dimension    | Main Question                             |
| ------------ | ----------------------------------------- |
| Accuracy     | Is the value correct?                     |
| Completeness | Is required information present?          |
| Consistency  | Is information represented consistently?  |
| Validity     | Does the value follow the required rules? |
| Uniqueness   | Are there unintended duplicate records?   |

---

## 3. Missing Values

A missing value occurs when a field does not contain a recorded value.

### Common Causes

- Information was not provided.
- A system failed to capture a value.
- Data was imported incorrectly.
- A field was optional.
- Information was lost during processing.

### Example

| Order ID | Product  |  Quantity |
| -------- | -------- | --------: |
| 101      | Laptop   |         2 |
| 102      | Mouse    |         5 |
| 103      | Keyboard | *(blank)* |

The quantity for Order 103 is missing.

### Methods for Handling Missing Values

1. **Check the original source:** Recover the correct value if reliable source information is available.
2. **Keep the value missing:** Preserve the blank when the correct value cannot be established.
3. **Estimate the value:** Use a justified statistical method when appropriate for the analysis.
4. **Exclude a record from a specific analysisgive m:** Do this only when the exclusion is justified and documented.

### Excel Formula to Count Blank Cells

```excel
=COUNTBLANK(C2:C6)
```

This formula counts blank cells in the specified range.

**Important:** Do not automatically replace every blank with zero. A missing quantity does not necessarily mean that zero items were sold.

---

## 4. Duplicate Records

A duplicate record occurs when the same record appears more than once when it should be represented only once.

### Example

| Order ID | Product  | Revenue |
| -------- | -------- | ------: |
| 101      | Laptop   |   80000 |
| 102      | Mouse    |    2500 |
| 102      | Mouse    |    2500 |
| 103      | Keyboard |    4500 |

Order 102 appears twice.

If both rows represent the same transaction, counting both may overstate total revenue.

### How to Highlight Duplicates in Excel

1. Select the Order ID column.
2. Go to **Home**.
3. Select **Conditional Formatting**.
4. Choose **Highlight Cells Rules**.
5. Select **Duplicate Values**.
6. Choose a formatting style.

### Excel Formula to Count Occurrences

```excel
=COUNTIF($A$2:$A$100,A2)
```

This formula counts how often the Order ID in cell A2 occurs in the specified range.

A result greater than 1 indicates a repeated ID, not necessarily a duplicate transaction.

### How to Remove Duplicates

1. Create a backup of the original dataset.
2. Select the dataset.
3. Open the **Data** tab.
4. Click **Remove Duplicates**.
5. Select the columns that define a duplicate.
6. Click **OK**.
7. Review the results.

**Important:** An Order ID can appear multiple times legitimately when an order contains several products. Always understand the dataset's unique key before removing records.

---

## 5. Cleaning Inconsistent Text

Text fields may contain inconsistent capitalization, unnecessary spaces, or spelling differences.

### Example

| Original Value | Issue                       |
| -------------- | --------------------------- |
| `Laptop`       | Standard format             |
| `laptop`       | Inconsistent capitalization |
| `LAPTOP`       | Extra spaces                |
| `Laptop `      | Trailing space              |
| `Keybord`      | Possible spelling error     |

These values can cause problems when grouping records or comparing categories.

### 5.1 TRIM()

Removes leading and trailing spaces and reduces repeated internal spaces to one space.

```excel
=TRIM(B2)
```

Example:

`"  Laptop   "` becomes `"Laptop"`.

### 5.2 PROPER()

Capitalizes the first letter of each word.

```excel
=PROPER(B2)
```

Example:

`"hyderabad"` becomes `"Hyderabad"`.

### 5.3 UPPER()

Converts text to uppercase.

```excel
=UPPER(B2)
```

Example:

`"laptop"` becomes `"LAPTOP"`.

### 5.4 LOWER()

Converts text to lowercase.

```excel
=LOWER(B2)
```

Example:

`"SALES@EXAMPLE.COM"` becomes `"sales@example.com"`.

### 5.5 Find and Replace

Find and Replace can correct verified spelling or naming inconsistencies.

Steps:

1. Press `Ctrl + H`.
2. Enter the incorrect value in **Find what**.
3. Enter the verified replacement in **Replace with**.
4. Review the replacements.
5. Apply the changes.

**Important:** Formatting text and correcting incorrect information are different operations. Corrections should follow verified source information or approved business rules.

---

## 6. Invalid Values and Business Rules

Invalid values do not follow the expected rules for a particular field or business process.

### Example

| Order ID | Quantity | Revenue |
| -------- | -------: | ------: |
| 201      |        2 |    5000 |
| 202      |       -3 |    2500 |
| 203      |        5 |   -1000 |
| 204      |        0 |    3000 |

Potential issues include:

- Negative quantity.
- Negative revenue.
- Zero quantity with positive revenue.

However, negative quantities or revenue may represent returns, refunds, or adjustments.

### Excel Formula to Flag Negative Quantities

```excel
=IF(C2<0,"Check Quantity","OK")
```

This formula flags negative quantities for investigation.

### Excel Formula to Identify Missing Order IDs

```excel
=IF(A2="","Missing Order ID","OK")
```

These formulas help identify potential issues, but they do not automatically determine whether a record is incorrect.

**Key takeaway:** Understand the business meaning of a value before changing it.

---

## 7. Incorrect Data Formats and Data Types

Sometimes values are stored in formats that prevent correct analysis.

### Examples

- Dates stored as text.
- Revenue stored as text instead of numbers.
- Numbers containing unwanted text characters.
- Customer IDs losing leading zeros.
- Different date formats used in the same dataset.

### Common Problems

| Problem                   | Possible Effect                        |
| ------------------------- | -------------------------------------- |
| Dates stored as text      | Incorrect sorting or date calculations |
| Revenue stored as text    | Incorrect or incomplete calculations   |
| Inconsistent date formats | Misinterpretation of dates             |
| Lost leading zeros in IDs | Incorrect identification or matching   |

### How to Handle These Issues

- Apply the correct date format.
- Confirm that numerical fields contain actual numbers.
- Use **Data → Text to Columns** when appropriate.
- Standardize date representations.
- Preserve identifiers as text when leading zeros are meaningful.

Consistent formats help Excel and other analytical tools interpret values correctly.

---

## 8. Outliers and Data Cleaning

An outlier is an observation that is unusually high or low compared with the other observations.

### Example

Daily sales:

1000, 1200, 1100, 950, 100000

The value 100000 is much higher than the other observations.

Possible explanations include:

- A genuine large transaction.
- A data-entry error.
- A special business event.
- An unusual transaction type.

### How to Handle Outliers

1. Identify the unusual value.
2. Compare it with related records.
3. Check the original source when possible.
4. Determine whether it is valid.
5. Decide how to handle it based on evidence and business requirements.
6. Document the decision.

**Important:** Do not automatically delete outliers. Unusual values may contain important business information.

---

## 9. Introduction to Power Query

Power Query is a data preparation and transformation tool available in Excel and Power BI.

It allows analysts to create repeatable steps for importing, cleaning, and transforming data.

### Common Power Query Operations

| Operation         | Purpose                                                       |
| ----------------- | ------------------------------------------------------------- |
| Remove Duplicates | Remove repeated records based on selected columns             |
| Remove Blank Rows | Remove entirely blank rows                                    |
| Trim              | Remove leading and trailing spaces                            |
| Clean             | Remove certain non-printable characters                       |
| Replace Values    | Replace specified values                                      |
| Change Type       | Set a column to the appropriate data type                     |
| Filter Rows       | Keep or exclude records based on conditions                   |
| Fill Down         | Propagate values into empty cells below them when appropriate |

### Why Is Power Query Useful?

Suppose a company sends a new sales file every week.

Instead of repeating the same cleaning operations manually, an analyst can save the transformation steps in Power Query and refresh them when new data arrives.

### Basic Workflow

**Import → Clean → Transform → Load → Refresh**

Power Query is an important foundation for future Power BI projects.

---

## 10. Data Cleaning Workflow

A professional Data Analyst follows a systematic cleaning process.

1. **Understand the dataset:** Identify the columns, their meanings, and business rules.
2. **Preserve the original data:** Keep an unchanged copy or backup.
3. **Profile the dataset:** Check missing values, duplicates, formats, and unusual values.
4. **Define cleaning rules:** Decide how each problem should be handled.
5. **Clean and transform:** Apply appropriate Excel formulas or Power Query operations.
6. **Validate the results:** Check row counts, totals, and important fields.
7. **Document the work:** Record the changes, decisions, and remaining limitations.

### Why Is Validation Important?

After cleaning, compare the original and cleaned datasets.

For example:

- Check row counts before and after removing duplicates.
- Compare revenue totals.
- Confirm that required fields are populated appropriately.
- Verify that date and numerical columns use suitable data types.
- Review the changes made to unusual values.

Validation helps prevent accidental data loss and incorrect reporting.



## 11. Practical Exercise: Clean a Sales Dataset

Use the following dataset to practice the concepts learned today.

| Order ID | Product    |  Quantity | Revenue (₹) |
| -------- | ---------- | --------: | ----------: |
| 201      | Laptop     |         2 |       80000 |
| 202      | mouse      |         5 |        2500 |
| 202      | mouse      |         5 |        2500 |
| 203      | `Keyboard` |         3 |        4500 |
| 204      | Monitor    | *(blank)* |       15000 |
| 205      | Mouse      |        -2 |        1000 |
| 206      | LAPTOP     |         1 |       40000 |

# Tasks

1. Identify repeated Order IDs.
2. Check whether repeated rows represent genuine duplicates.
3. Standardize product names.
4. Remove unnecessary spaces.
5. Investigate the missing quantity for Order 204.
6. Investigate the negative quantity for Order 205.
7. Decide whether `Laptop` and `LAPTOP` should be grouped together.
8. Check the data types of Quantity and Revenue.
9. Compare row counts and revenue totals before and after cleaning.
10. Document the cleaning decisions.

# Important Notes

- Do not fill missing quantities without reliable evidence.
- Do not automatically delete negative quantities.
- Verify duplicate records before removing them.
- Standardize product names using consistent rules.
- Keep the original dataset unchanged.

# Expected Learning Outcome

After completing this exercise, I should be able to identify common data-quality problems, clean data responsibly, and explain why each cleaning decision was made.


## 12. Key Takeaways

- Data cleaning prepares raw data for reliable analysis.
- Data quality includes accuracy, completeness, consistency, validity, and uniqueness.
- Missing values require investigation and an appropriate treatment.
- Duplicate records can lead to incorrect calculations.
- `TRIM()`, `PROPER()`, `UPPER()`, and `LOWER()` help standardize text.
- `COUNTIF()` helps identify repeated values.
- `COUNTBLANK()` counts missing cells.
- `IF()` can flag values that require investigation.
- Incorrect data formats can affect sorting and calculations.
- Outliers should be investigated before making changes.
- Power Query supports repeatable data transformation.
- Validation helps confirm that cleaning operations worked as intended.
- Documenting decisions improves transparency and reproducibility.

## 13. Day 5 Completion Checklist

- [ ] Understood data cleaning and data quality.
- [ ] Learned the major dimensions of data quality.
- [ ] Practiced identifying missing values.
- [ ] Practiced detecting duplicate records.
- [ ] Learned Excel text-cleaning functions.
- [ ] Identified invalid values using business rules.
- [ ] Understood data-format problems.
- [ ] Learned how to investigate outliers.
- [ ] Explored Power Query operations.
- [ ] Completed the sales data-cleaning exercise.
- [ ] Learned to validate and document cleaning decisions.



# Tools and Technologies

- Microsoft Excel
- Power Query
- Markdown
- Git and GitHub

