# Day 09: Data Transformation

## 1. Introduction

Data Transformation is an important step in the Data Analytics process. It involves converting raw data into a structured, consistent, and analysis-ready format.

In real-world businesses, data is collected from different sources, such as Excel files, databases, CSV files, and business applications. This data may contain inconsistent formats, incorrect data types, or structures that are difficult to analyze.

Data transformation helps Data Analysts prepare this data for calculations, reporting, visualization, and decision-making.

**Objective:** Understand the fundamentals of data transformation and learn how to prepare raw data for analysis using Excel, SQL, Python, and Power Query.

---

## 2. What Is Data Transformation?

Data transformation is the process of changing the format, structure, or representation of data to make it suitable for analysis.

### Example

Original sales data:

| Product | Quantity | Unit Price |
|---|---:|---:|
| Laptop | 2 | 40000 |
| Mouse | 3 | 500 |
| Keyboard | 1 | 1200 |

After transformation, we calculate Revenue.

**Formula:**

`Revenue = Quantity × Unit Price`

Transformed data:

| Product | Quantity | Unit Price | Revenue |
|---|---:|---:|---:|
| Laptop | 2 | 40000 | 80000 |
| Mouse | 3 | 500 | 1500 |
| Keyboard | 1 | 1200 | 1200 |

The new Revenue column makes it easier to analyze the financial performance of products.

---

## 3. Why Is Data Transformation Important?

Data transformation is important because it:

- Improves data consistency.
- Converts values into appropriate data types.
- Supports accurate calculations.
- Makes data easier to analyze.
- Helps combine data from multiple sources.
- Improves the quality of reports and dashboards.
- Reduces repetitive manual work through reusable processes.

For example, a company may receive sales data in different date formats. Standardizing the dates allows analysts to group sales by month and identify business trends.

---

## 4. Data Cleaning vs. Data Transformation

Data cleaning and data transformation are related but different processes.

| Data Cleaning | Data Transformation |
|---|---|
| Identifies and corrects data quality problems. | Changes the format or structure of data. |
| Removes unwanted duplicates when appropriate. | Creates new calculated columns. |
| Handles missing or invalid values. | Converts data types and standardizes formats. |
| Corrects inaccurate records. | Reshapes and aggregates data. |

**Example:**

- Removing an invalid transaction is data cleaning.
- Converting a text date into a valid date value is data transformation.
- Both operations may be needed before creating a reliable sales report.

---

## 5. Types of Data Transformation

### 5.1 Data Type Conversion

Data type conversion changes a value from one data type to another.

Common data types include:

- Integer: `100`
- Decimal: `99.50`
- Text/String: `"Laptop"`
- Date: `2026-10-17`
- Boolean: `TRUE` or `FALSE`

Example:

A Quantity value stored as text may need to be converted into a number before calculating total sales.

Important: IDs such as `00125` should often remain text to preserve leading zeros.

### 5.2 Data Standardization

Standardization makes data consistent across records.

Example:

Original values:

- `Hyderabad`
- `HYDERABAD`
- `hyderabad`
- ` Hyderabad `

Standardized value:

- `Hyderabad`

Useful Excel formulas:

```excel
=TRIM(A2)
=PROPER(TRIM(A2))
```

`TRIM()` removes unnecessary spaces, while `PROPER()` converts text into title case. Always verify the result for abbreviations and special names.

### 5.3 Creating Calculated Columns

Calculated columns derive new values from existing columns.

Common business formulas:

- Revenue = Quantity × Unit Price
- Profit = Revenue − Cost
- Discount Amount = Original Price × Discount Rate

Excel example:

```excel
=B2*C2
```

This formula calculates Revenue when B2 contains Quantity and C2 contains Unit Price.

Calculated columns help analysts answer business questions without manually calculating every record.

### 5.4 Splitting and Merging Columns

Sometimes a column contains multiple pieces of information.

Example:

Original column:

| Full Name |
|---|
| Ravi Kumar |
| Priya Sharma |

After splitting:

| First Name | Last Name |
|---|---|
| Ravi | Kumar |
| Priya | Sharma |

Columns can also be merged to combine related information.

Tools and methods include Excel Text to Columns, Flash Fill, formulas, and Power Query's Split Column and Merge Columns features.

### 5.5 Date Transformation

Date transformation standardizes dates and prepares them for time-based analysis.

Examples of date representations:

- `17/10/2026`
- `10/17/2026`
- `2026-10-17`

The intended date must be interpreted correctly before standardization.

Excel formula for extracting the month name from a valid date in A2:

```excel
=TEXT(A2,"mmmm")
```

Date transformation helps analysts calculate monthly revenue, compare years, and identify seasonal trends.

### 5.6 Filtering and Selecting Data

Filtering selects records that meet specific conditions.

Example: A business wants to analyze completed orders only.

| Order ID | Status | Revenue |
|---|---|---:|
| 101 | Completed | 5000 |
| 102 | Pending | 3000 |
| 103 | Completed | 7000 |

After filtering for Completed orders, the revenue is:

`5000 + 7000 = 12000`

Filtering does not necessarily delete records; it selects the records needed for the current analysis.

### 5.7 Aggregation and Summarization

Aggregation combines detailed records into summarized results.

Example:

| Region | Revenue |
|---|---:|
| South | 5000 |
| North | 3000 |
| South | 7000 |
| North | 2000 |

Summarized result:

| Region | Total Revenue |
|---|---:|
| South | 12000 |
| North | 5000 |

Common aggregation functions:

- `SUM()` — calculates a total.
- `COUNT()` — counts records or values, depending on the function.
- `AVG()` — calculates an average in SQL.
- `MIN()` — returns the minimum value.
- `MAX()` — returns the maximum value.

Aggregation is useful for sales reports, regional comparisons, and dashboards.

### 5.8 Data Reshaping

Data reshaping changes how data is organized.

Wide format:

| Product | January | February | March |
|---|---:|---:|---:|
| Laptop | 10 | 12 | 15 |
| Mouse | 20 | 25 | 30 |

Long format:

| Product | Month | Units Sold |
|---|---|---:|
| Laptop | January | 10 |
| Laptop | February | 12 |
| Laptop | March | 15 |
| Mouse | January | 20 |
| Mouse | February | 25 |
| Mouse | March | 30 |

Long-format data is often easier to filter, group, visualize, and analyze across multiple periods.

In Power Query, this can be done using **Unpivot Columns**.

---

## 6. Data Transformation Using Different Tools

| Transformation | Excel | SQL | Power Query |
|---|---|---|---|
| Convert data types | Format or functions | `CAST()` | Change Type |
| Standardize text | `TRIM()`, `UPPER()` | `TRIM()`, `UPPER()` | Format options |
| Calculate revenue | Excel formulas | SQL expressions | Custom Column |
| Filter rows | Filter dropdown | `WHERE` | Filter Rows |
| Summarize data | PivotTable | `GROUP BY` | Group By |
| Reshape data | Power Query | Depends on query and database | Pivot / Unpivot |

Python can also perform these operations using libraries such as Pandas.

### SQL Example

```sql
SELECT
    product,
    quantity,
    unit_price,
    quantity * unit_price AS revenue
FROM sales;
```

Explanation:

1. Reads data from the `sales` table.
2. Selects the required columns.
3. Calculates revenue for each row.
4. Returns the calculated value under the name `revenue`.

This query calculates revenue in the result; it does not permanently create a column in the source table.

### Python Example Using Pandas

```python
import pandas as pd

df = pd.DataFrame({
    "product": ["Laptop", "Mouse", "Keyboard"],
    "quantity": [2, 3, 1],
    "unit_price": [40000, 500, 1200]
})

df["revenue"] = df["quantity"] * df["unit_price"]

print(df)
```

Expected Revenue values:

- Laptop: 80000
- Mouse: 1500
- Keyboard: 1200

---

## 7. Data Transformation in Power BI

Power BI uses Power Query to import, clean, and transform data before loading it into the data model.

### Steps

1. Open Power BI Desktop.
2. Select **Get Data**.
3. Import an Excel or CSV file.
4. Select **Transform Data** to open Power Query Editor.
5. Correct data types.
6. Remove unnecessary columns or rows.
7. Standardize text and date formats.
8. Create calculated columns or combine datasets when needed.
9. Validate the transformed data.
10. Select **Close & Apply**.

Power Query stores transformations as Applied Steps. During refresh, these steps can be executed again on updated source data.

This makes the data preparation process repeatable and reduces manual work.

---

## 8. Practical Exercise: Sales Data Transformation

### Raw Dataset

| Order ID | City | Quantity | Unit Price |
|---|---|---:|---:|
| 101 | ` hyderabad ` | 2 | 1000 |
| 102 | `CHENNAI` | 3 | 500 |
| 103 | `Hyderabad` | 1 | 2000 |
| 104 | `chennai ` | 4 | 250 |

### Tasks

1. Standardize city names.
2. Create a Revenue column.
3. Calculate total revenue.
4. Calculate revenue by city.
5. Verify all calculations.

### Expected Results

| Order ID | City | Quantity | Unit Price | Revenue |
|---|---|---:|---:|---:|
| 101 | Hyderabad | 2 | 1000 | 2000 |
| 102 | Chennai | 3 | 500 | 1500 |
| 103 | Hyderabad | 1 | 2000 | 2000 |
| 104 | Chennai | 4 | 250 | 1000 |

Total Revenue:

`2000 + 1500 + 2000 + 1000 = 6500`

Revenue by City:

| City | Total Revenue |
|---|---:|
| Hyderabad | 4000 |
| Chennai | 2500 |

### Business Insight

Hyderabad generated 4000 in revenue, while Chennai generated 2500. In this sample, Hyderabad generated more revenue than Chennai.

This simple analysis demonstrates how data transformation prepares transaction-level data for meaningful business comparisons.

---

## 9. Common Data Transformation Mistakes

1. Changing data without understanding the business meaning.
2. Converting identifiers into numbers and losing leading zeros.
3. Misinterpreting date formats.
4. Removing legitimate duplicate transactions.
5. Replacing missing values with zero without justification.
6. Forgetting to verify calculations after transformation.
7. Overwriting raw data without retaining an original copy.
8. Combining datasets without checking column meanings and data types.

**Best practice:** Preserve the original data when possible, document transformations, and validate the results before reporting.

---

## 10. Day 09 Learning Outcomes

After completing Day 09, I understand:

- The meaning and importance of data transformation.
- The difference between data cleaning and data transformation.
- Data type conversion and standardization.
- Creating calculated columns using formulas.
- Splitting and merging columns.
- Date transformation.
- Filtering and selecting data.
- Aggregation and summarization.
- Wide and long data formats.
- Basic SQL and Python transformation concepts.
- The Power Query workflow in Power BI.
- Validating transformed data before analysis.

---

## 11. Conclusion

Data transformation is a fundamental skill for every Data Analyst. Raw data often needs to be standardized, converted, calculated, filtered, summarized, or reshaped before it can support reliable analysis.
