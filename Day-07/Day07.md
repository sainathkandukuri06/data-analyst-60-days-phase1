# Day 07: Excel Formulas and Functions for Data Analysis

# Learning Objectives

- Understand Excel formulas, functions, cell references, and ranges.
- Use basic functions such as `SUM`, `AVERAGE`, `COUNT`, `COUNTA`, `MIN`, and `MAX`.
- Calculate revenue, profit, and profit margin.
- Understand relative, absolute, and mixed cell references.
- Apply conditional functions such as `SUMIF`, `SUMIFS`, `COUNTIF`, and `COUNTIFS`.
- Use logical functions such as `IF`, `AND`, and `OR`.
- Handle formula errors using `IFERROR`.
- Clean and standardize text using Excel text functions.
- Round numerical values and calculate percentages.
- Build a simple sales analysis report.


# 1. Understanding Excel Formulas and Functions

# What Is an Excel Formula?

An Excel formula is an expression used to perform calculations using values, cell references, operators, and functions.

Example:

```excel
=B2+B3
```

If B2 contains 1000 and B3 contains 500, the result is 1500.

### What Is an Excel Function?

A function is a predefined calculation built into Excel.

Example:

```excel
=SUM(B2:B10)
```

This adds all numeric values in cells B2 through B10.

### Important Terms

| Term | Meaning | Example |
|---|---|---|
| Formula | An expression used for calculation | `=B2+B3` |
| Function | A built-in Excel calculation | `=SUM(B2:B10)` |
| Cell reference | Address of a cell | `B2` |
| Range | A group of cells | `B2:B10` |
| Operator | Symbol used in calculations or comparisons | `+`, `-`, `*`, `/`, `>` |

Excel recalculates formulas when their referenced values change, provided automatic calculation is enabled.

---

## 2. Practice Dataset

The following sample sales dataset is used for this challenge.

| Order ID | Product | City | Units | Unit Price (₹) | Cost per Unit (₹) |
|---|---|---|---:|---:|---:|
| 101 | Laptop | Hyderabad | 2 | 40000 | 32000 |
| 102 | Mouse | Chennai | 5 | 800 | 500 |
| 103 | Phone | Hyderabad | 3 | 20000 | 15000 |
| 104 | Keyboard | Bengaluru | 4 | 1500 | 900 |
| 105 | Laptop | Chennai | 1 | 40000 | 32000 |
| 106 | Monitor | Bengaluru | 2 | 12000 | 9000 |

### Additional Columns

I added two calculated columns:

- Revenue
- Profit

The final dataset contains:

| Column | Description |
|---|---|
| A | Order ID |
| B | Product |
| C | City |
| D | Units |
| E | Unit Price |
| F | Cost per Unit |
| G | Revenue |
| H | Profit |

---

## 3. Basic Excel Functions

### A. SUM()

**Purpose:** Calculates the total of numeric values.

Formula:

```excel
=SUM(G2:G7)
```

Expected result: `214000`

Business application: Calculate total revenue, cost, or profit.

### B. AVERAGE()

**Purpose:** Calculates the arithmetic mean of numeric values.

Formula:

```excel
=AVERAGE(G2:G7)
```

Expected result: `35666.67`

Business application: Calculate average revenue per order.

### C. COUNT()

**Purpose:** Counts cells containing numeric values.

Formula:

```excel
=COUNT(G2:G7)
```

Expected result: `6`

Business application: Count numeric entries in a column.

### D. COUNTA()

**Purpose:** Counts non-empty cells.

Formula:

```excel
=COUNTA(A2:A7)
```

Expected result: `6`

Business application: Count populated order IDs.

### E. MIN()

**Purpose:** Returns the smallest numeric value.

Formula:

```excel
=MIN(G2:G7)
```

Expected result: `4000`

Business application: Identify the lowest order revenue.

### F. MAX()

**Purpose:** Returns the largest numeric value.

Formula:

```excel
=MAX(G2:G7)
```

Expected result: `80000`

Business application: Identify the highest order revenue.

### Function Summary

| Function | Purpose |
|---|---|
| `SUM` | Calculate totals |
| `AVERAGE` | Calculate averages |
| `COUNT` | Count numeric values |
| `COUNTA` | Count non-empty cells |
| `MIN` | Find the minimum |
| `MAX` | Find the maximum |

**Important:** `COUNT()` counts numeric cells, while `COUNTA()` counts non-empty cells. They are useful for different purposes.

---

## 4. Calculating Revenue

### What Is Revenue?

Revenue is the amount generated from selling goods or services before deducting costs and expenses.

### Formula

Revenue is calculated as:

**Revenue = Units Sold × Unit Price**

For Order 101:

- Units sold = 2
- Unit price = ₹40,000

Calculation:

`2 × 40000 = ₹80000`

Excel formula in cell G2:

```excel
=D2*E2
```

Copy the formula down from G2 to G7.

### Expected Revenue Results

| Order ID | Product | Revenue (₹) |
|---|---|---:|
| 101 | Laptop | 80000 |
| 102 | Mouse | 4000 |
| 103 | Phone | 60000 |
| 104 | Keyboard | 6000 |
| 105 | Laptop | 40000 |
| 106 | Monitor | 24000 |
| **Total** | | **214000** |

Total revenue:

```excel
=SUM(G2:G7)
```

Expected result: `214000`

---

## 5. Calculating Profit

### What Is Profit?

Profit is the difference between revenue and the costs associated with generating that revenue.

For this exercise, profit means revenue minus the cost of the units sold. Other business expenses are not included.

### Formulas

Total Cost:

**Total Cost = Units Sold × Cost per Unit**

Profit:

**Profit = Revenue − Total Cost**

For Order 101:

- Revenue = ₹80,000
- Units sold = 2
- Cost per unit = ₹32,000
- Total cost = ₹64,000

Calculation:

`80000 - (2 × 32000) = 16000`

Excel formula in cell H2:

```excel
=G2-(D2*F2)
```

Copy the formula down from H2 to H7.

### Expected Profit Results

| Order ID | Revenue (₹) | Profit (₹) |
|---|---:|---:|
| 101 | 80000 | 16000 |
| 102 | 4000 | 1500 |
| 103 | 60000 | 15000 |
| 104 | 6000 | 2400 |
| 105 | 40000 | 8000 |
| 106 | 24000 | 6000 |
| **Total** | **214000** | **48900** |

Total profit:

```excel
=SUM(H2:H7)
```

Expected result: `48900`

---

## 6. Calculating Profit Margin

### Definition

Profit margin measures the percentage of revenue that remains as profit.

### Formula

**Profit Margin = (Profit / Revenue) × 100**

For Order 101:

`(16000 / 80000) × 100 = 20%`

Excel formula:

```excel
=H2/G2
```

Format the cell as Percentage.

### Overall Profit Margin

The overall profit margin is calculated using total profit divided by total revenue.

```excel
=SUM(H2:H7)/SUM(G2:G7)
```

Expected result: approximately `22.85%`

**Important:** The overall profit margin is not necessarily equal to the simple average of the individual order margins.

This example does not include all business expenses, so it should not be interpreted as net profit margin.

---

## 7. Relative, Absolute, and Mixed Cell References

Cell references determine how formulas behave when they are copied to other cells.

### A. Relative Reference

Example:

```excel
=D2*E2
```

When copied down one row, it changes to:

```excel
=D3*E3
```

Both row references adjust automatically.

### B. Absolute Reference

Suppose the commission rate is stored in K1 and the revenue is in G2.

Formula:

```excel
=G2*$K$1
```

When copied down, the formula becomes:

```excel
=G3*$K$1
```

The revenue reference changes, but K1 remains fixed.

### C. Mixed Reference

- `$K1` locks the column.
- `K$1` locks the row.

### Comparison

| Reference Type | Example | Behavior |
|---|---|---|
| Relative | `A1` | Row and column can change |
| Absolute | `$A$1` | Row and column remain fixed |
| Mixed | `$A1` | Column remains fixed |
| Mixed | `A$1` | Row remains fixed |

**Practical tip:** On many Windows keyboards, pressing F4 while editing a cell reference cycles through reference styles.

---

## 8. Conditional Functions

Conditional functions perform calculations only when specified conditions are satisfied.

### A. SUMIF()

**Purpose:** Adds values that satisfy one condition.

Syntax:

```excel
=SUMIF(criteria_range,criteria,sum_range)
```

Example: Calculate Hyderabad revenue.

```excel
=SUMIF(C2:C7,"Hyderabad",G2:G7)
```

Expected result: `140000`

Explanation:

- `C2:C7` contains city names.
- `"Hyderabad"` is the condition.
- `G2:G7` contains the revenue values to add.

### B. SUMIFS()

**Purpose:** Adds values that satisfy multiple conditions.

Example: Calculate Laptop revenue in Chennai.

```excel
=SUMIFS(G2:G7,B2:B7,"Laptop",C2:C7,"Chennai")
```

Expected result: `40000`

Conditions:

- Product = Laptop
- City = Chennai

Both conditions must be satisfied.

### C. COUNTIF()

**Purpose:** Counts cells satisfying one condition.

Example: Count orders from Bengaluru.

```excel
=COUNTIF(C2:C7,"Bengaluru")
```

Expected result: `2`

### D. COUNTIFS()

**Purpose:** Counts records satisfying multiple conditions.

Example: Count Laptop orders in Chennai.

```excel
=COUNTIFS(B2:B7,"Laptop",C2:C7,"Chennai")
```

Expected result: `1`

### Function Comparison

| Function | Purpose |
|---|---|
| `SUMIF` | Sum values using one condition |
| `SUMIFS` | Sum values using multiple conditions |
| `COUNTIF` | Count matching cells using one condition |
| `COUNTIFS` | Count matching records using multiple conditions |

**Important:** `SUMIF()` uses the criteria range first, while `SUMIFS()` uses the sum range first.

---

## 9. Logical Functions

Logical functions help Excel make decisions based on business rules.

### A. IF()

**Purpose:** Returns one result if a condition is true and another if it is false.

Syntax:

```excel
=IF(condition,value_if_true,value_if_false)
```

Example: Classify orders with revenue of at least ₹30,000 as High Value.

```excel
=IF(G2>=30000,"High Value","Normal")
```

Possible results:

- Revenue ≥ ₹30,000 → High Value
- Revenue < ₹30,000 → Normal

### B. AND()

**Purpose:** Returns TRUE when all specified conditions are true.

Example: Revenue must be at least ₹30,000 and profit must be at least ₹10,000.

```excel
=IF(AND(G2>=30000,H2>=10000),"Qualifies","Does Not Qualify")
```

Both conditions must be satisfied.

### C. OR()

**Purpose:** Returns TRUE when at least one condition is true.

Example: Mark an order for review if revenue exceeds ₹70,000 or profit exceeds ₹14,000.

```excel
=IF(OR(G2>70000,H2>14000),"Review","Normal")
```

At least one condition must be satisfied.

### Logical Function Comparison

| Function | Purpose |
|---|---|
| `IF` | Make a decision based on a condition |
| `AND` | Require all conditions to be true |
| `OR` | Require at least one condition to be true |

---

## 10. Error Handling with IFERROR()

### Definition

`IFERROR()` returns a specified alternative value when a formula produces an error.

### Common Excel Errors

| Error | Meaning |
|---|---|
| `#DIV/0!` | Division by zero |
| `#VALUE!` | Invalid value or data type |
| `#REF!` | Invalid cell reference |
| `#NAME?` | Unrecognized function or name |

### Example

Profit margin calculation:

```excel
=IFERROR(H2/G2,"Check Data")
```

If the calculation succeeds, Excel returns the profit margin.

If the calculation produces an error, Excel displays `Check Data`.

Another approach when zero revenue is a known possibility:

```excel
=IF(G2=0,"N/A",H2/G2)
```

**Best practice:** Error handling should help users interpret a report without hiding underlying data problems.


# 11. Text Functions for Data Cleaning

Text functions help standardize inconsistent text values.

# A. TRIM()

Removes extra spaces between words and at the beginning or end of text.

```excel
=TRIM(A2)
```

Example:

`"  Hyderabad   "` becomes `"Hyderabad"`.

# B. UPPER()

Converts text to uppercase.

```excel
=UPPER(B2)
```

Example: `Laptop` becomes `LAPTOP`.

# C. LOWER()

Converts text to lowercase.

```excel
=LOWER(B2)
```

Example: `Laptop` becomes `laptop`.

# D. PROPER()

Capitalizes the first letter of each word.

```excel
=PROPER(B2)
```

Example: `wireless mouse` becomes `Wireless Mouse`.

# E. CONCAT()

Combines text values.

```excel
=CONCAT(A2,"-",B2)
```

Example: `Order` and `101` can be combined into `Order-101`.

# Business Applications

- Standardize city names.
- Clean product descriptions.
- Remove unwanted spaces.
- Improve consistency in text fields.
- Create readable labels for reports.

These functions help improve consistency, but they should be applied carefully to preserve official names, acronyms, and product codes.

# 12. Rounding and Percentage Formatting

# ROUND()

**Purpose:** Rounds a number to a specified number of digits.

Syntax:

```excel
=ROUND(number,num_digits)
```

Example:

```excel
=ROUND(35666.6667,2)
```

Expected result: `35666.67`

Round to a whole number:

```excel
=ROUND(35666.6667,0)
```

Expected result: `35667`

# Percentage Formatting

For a profit margin formula:

```excel
=H2/G2
```

Format the result as Percentage to display the value as a percentage.

For the overall profit margin:

```excel
=SUM(H2:H7)/SUM(G2:G7)
```

Expected result: approximately `22.85%`.

Percentage formatting changes how the result is displayed; it does not change the underlying calculation.

# 13. Mini Sales Analysis Report

After applying the formulas, the following results are obtained.

| Metric | Result |
|---|---:|
| Total Revenue | ₹214000 |
| Total Profit | ₹48900 |
| Average Order Revenue | ₹35666.67 |
| Highest Order Revenue | ₹80000 |
| Lowest Order Revenue | ₹4000 |
| Hyderabad Revenue | ₹140000 |
| Chennai Order Count | 2 |
| Laptop Revenue in Chennai | ₹40000 |
| Overall Profit Margin | 22.85% |

# Business Insights

1. The dataset generated total revenue of ₹2,14,000.
2. Total profit, based on the included product costs, is ₹48,900.
3. Hyderabad generated the highest revenue among the three cities, at ₹1,40,000.
4. The average revenue per order is approximately ₹35,666.67.
5. The overall profit margin is approximately 22.85%.

These findings describe the sample dataset. Additional data would be required to determine why performance differs across cities or products.


# 14. Practical Exercises

Complete these tasks in Excel.

- [ ] Create the sales dataset.
- [ ] Calculate revenue for all six orders.
- [ ] Calculate profit for all six orders.
- [ ] Calculate the profit margin for Order 101.
- [ ] Calculate total revenue using `SUM()`.
- [ ] Calculate average revenue using `AVERAGE()`.
- [ ] Find the highest and lowest revenue using `MAX()` and `MIN()`.
- [ ] Calculate Hyderabad revenue using `SUMIF()`.
- [ ] Count Chennai orders using `COUNTIF()`.
- [ ] Calculate Laptop revenue in Chennai using `SUMIFS()`.
- [ ] Use `IF()` to classify orders as High Value or Normal.
- [ ] Calculate the overall profit margin.
- [ ] Write three business insights based on your results.


# 15. Key Learnings

In Day 07, I learned:

- Excel formulas and built-in functions.
- Basic aggregation functions.
- Revenue, profit, and profit margin calculations.
- Relative, absolute, and mixed cell references.
- Conditional calculations using `SUMIF`, `SUMIFS`, `COUNTIF`, and `COUNTIFS`.
- Logical decisions using `IF`, `AND`, and `OR`.
- Error handling using `IFERROR`.
- Text cleaning using `TRIM`, `UPPER`, `LOWER`, `PROPER`, and `CONCAT`.
- Numerical rounding and percentage formatting.
- How to create a basic sales analysis report and interpret its results.

# 16. Conclusion

Excel formulas and functions are essential tools for Data Analysts. They automate calculations, reduce repetitive manual work, and help transform raw data into meaningful business information.

The concepts learned today provide a foundation for advanced Excel analysis, SQL aggregation, Python data analysis, and Power BI reporting.

*Day 07 Status:* Completed the study and practice of Excel formulas and functions as part of my 60-Day Data Analyst Challenge.

*Next Step:* Continue to Day 08 and build on these foundational data analysis skills.

# Repository Information

- **Repository:** `data-analyst-60-days-phase1`
- **Suggested file path:** `Day-07/README.md`
- **Tools Used:** Microsoft Excel
- **Skills Practiced:** Excel Formulas, Data Analysis, Conditional Functions, Logical Functions, Data Cleaning, Financial Calculations, and Business Reporting.
