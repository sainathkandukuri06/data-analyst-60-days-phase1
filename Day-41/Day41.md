# Day 41 – Excel Fundamentals for Data Analysts

Microsoft Excel is one of the most important tools used by Data Analysts to organize, clean, calculate, filter, and analyze large datasets.

In this session, I learned about sorting, filtering, Excel Tables, cell references, and basic Excel formulas.

## 1. Sorting Data

Sorting is the process of arranging data in a specific order based on one or more columns.

### Types of Sorting

- **Ascending Order:** Arranges data from smallest to largest or A to Z.
- **Descending Order:** Arranges data from largest to smallest or Z to A.

### Example

| Employee | Salary |
|---|---:|
| Ravi | 25000 |
| Suresh | 40000 |
| Kumar | 30000 |

After sorting salaries in descending order:

| Employee | Salary |
|---|---:|
| Suresh | 40000 |
| Kumar | 30000 |
| Ravi | 25000 |

**Real-world application:** Sorting helps analysts identify top-performing employees, highest-selling products, and highest-revenue customers.

---

## 2. Filtering Data

Filtering is used to display only the records that satisfy specific conditions while temporarily hiding other records.

### Example

Suppose a company has 100 employee records. We want to display only employees whose salary is greater than ₹30,000.

We can apply a filter to the Salary column and select the condition:

`Salary > 30000`

Excel displays only the matching employee records.

**Real-world application:**
- Finding employees from a specific department.
- Identifying customers from a particular city.
- Finding products with low sales.
- Analyzing transactions above a specific amount.

---

## 3. Excel Tables

An Excel Table is a structured format used to organize and manage datasets.

### Steps to Create an Excel Table

1. Select the complete dataset.
2. Press `Ctrl + T`.
3. Enable the option "My table has headers".
4. Click OK.

### Advantages

- Automatically provides filtering options.
- Applies consistent formatting.
- Expands automatically when new rows are added.
- Makes formulas easier to manage.
- Supports structured references.

**Real-world application:** Excel Tables are useful when working with regularly updated sales, employee, customer, and financial datasets.

---

## 4. Relative Cell References

A relative cell reference changes automatically when a formula is copied to another cell.

### Example

```excel
=A2+B2
```

When copied from cell C2 to C3, Excel automatically changes the formula to:

```excel
=A3+B3
```

**Purpose:** Relative references are useful when performing the same calculation across multiple rows or columns.

---

## 5. Absolute Cell References

An absolute cell reference remains fixed even when a formula is copied to another cell.

The dollar sign `$` is used to lock both the column and row.

### Example

```excel
=A2*$B$1
```

Here:
- `A2` is a relative reference.
- `$B$1` is an absolute reference.

Even if we copy the formula to another row, the reference `$B$1` remains unchanged.

**Real-world application:** Absolute references are useful for calculating fixed tax rates, discounts, commission percentages, and bonuses.

---

## 6. Basic Excel Formulas

Excel formulas help Data Analysts perform calculations and summarize information quickly.

| Formula | Description |
|---|---|
| `=SUM(A1:A10)` | Calculates the total of selected values. |
| `=AVERAGE(A1:A10)` | Calculates the average value. |
| `=COUNT(A1:A10)` | Counts cells containing numbers. |
| `=COUNTA(A1:A10)` | Counts non-empty cells. |
| `=MAX(A1:A10)` | Finds the highest value. |
| `=MIN(A1:A10)` | Finds the lowest value. |

### Example

Suppose the sales values are:

| Sales |
|---:|
| 1000 |
| 2000 |
| 3000 |

To calculate total sales:

```excel
=SUM(A2:A4)
```

**Result:** 6000

To calculate average sales:

```excel
=AVERAGE(A2:A4)
```

**Result:** 2000

---

## 7. Practical Applications in Data Analytics

The concepts learned today are useful in real-world Data Analyst tasks.

- Sorting helps identify the highest and lowest values.
- Filtering helps extract specific records from large datasets.
- Excel Tables help organize structured data.
- Relative references help automate repeated calculations.
- Absolute references help maintain fixed values in formulas.
- Basic formulas help calculate totals, averages, minimums, and maximums.

---

## 8. Key Learnings

Today, I learned:

1. How to sort data in ascending and descending order.
2. How to filter records based on specific conditions.
3. How to convert normal datasets into Excel Tables.
4. The difference between relative and absolute cell references.
5. How to use basic Excel formulas.
6. How Excel supports everyday Data Analyst activities.

---

## Conclusion

Excel is an essential tool for every Data Analyst. Understanding these fundamentals helps build a strong foundation for advanced Excel techniques, data cleaning, data analysis, and reporting.

**Day 41 Completed Successfully!** 🚀

#DataAnalytics #Excel #DataAnalyst #ExcelFundamentals #60DaysChallenge #LearningJourney