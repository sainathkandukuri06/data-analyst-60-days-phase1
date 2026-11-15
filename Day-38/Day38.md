# Day 38 – Intermediate DAX Functions in Power BI

## 1. CALCULATE() Function

### Definition
The `CALCULATE()` function evaluates an expression after modifying the filter context.

It is one of the most important functions in DAX because it allows us to calculate values based on specific conditions.

### Syntax
```dax
CALCULATE(
    Expression,
    Filter1,
    Filter2
)
```

### Example
```dax
South Sales =
CALCULATE(
    SUM(Sales[Amount]),
    Sales[Region] = "South"
)
```

### Explanation
- `SUM(Sales[Amount])` calculates total sales.
- `Sales[Region] = "South"` applies a condition.
- `CALCULATE()` evaluates the total sales only for the South region.

**Result:** Displays the total sales of the South region.

### Real-World Application
A company can use CALCULATE() to compare sales across different regions, products, and departments.

---

## 2. FILTER() Function

### Definition
The `FILTER()` function returns a table containing only the rows that satisfy a given condition.

It is useful when we need to apply specific conditions to a dataset.

### Syntax
```dax
FILTER(
    Table,
    Condition
)
```

### Example
```dax
High Sales =
CALCULATE(
    SUM(Sales[Amount]),
    FILTER(
        Sales,
        Sales[Amount] > 10000
    )
)
```

### Explanation
- `Sales` represents the table.
- `Sales[Amount] > 10000` checks the condition.
- FILTER() returns only the rows where sales are greater than 10,000.
- CALCULATE() calculates the total amount from those rows.

**Result:** Calculates total sales for transactions greater than 10,000.

### Real-World Application
Businesses can identify high-value transactions, profitable customers, and important sales records.

---

## 3. ALL() Function

### Definition
The `ALL()` function removes filters from a specified table or column.

It is useful when we want to calculate an overall total without being affected by certain filters.

### Syntax
```dax
ALL(Table)
```

### Example
```dax
Total Sales =
CALCULATE(
    SUM(Sales[Amount]),
    ALL(Sales)
)
```

### Explanation
- SUM() calculates the total sales amount.
- ALL(Sales) removes filters from the Sales table.
- CALCULATE() evaluates the calculation without those table filters.

**Result:** Returns the overall sales total, regardless of filters on the Sales table.

### Real-World Application
ALL() is useful for calculating overall company sales, comparing regional performance, and calculating percentages of total sales.

---

## 4. RELATED() Function

### Definition
The `RELATED()` function retrieves a value from another related table using an existing relationship between tables.

It is commonly used when working with multiple tables in a Power BI data model.

### Syntax
```dax
RELATED(TableName[ColumnName])
```

### Example

Suppose we have two tables:

**Sales Table**

| ProductID | Quantity |
|---|---:|
| 101 | 5 |
| 102 | 3 |
| 103 | 8 |

**Products Table**

| ProductID | ProductName | Price |
|---|---|---:|
| 101 | Laptop | 50000 |
| 102 | Mouse | 500 |
| 103 | Keyboard | 1500 |

DAX Formula:

```dax
Product Price =
RELATED(Products[Price])
```

### Explanation
- Sales and Products tables must have an appropriate relationship.
- RELATED() uses that relationship to retrieve the matching product price.
- The value is returned for each corresponding row in the Sales table.

**Result:** Retrieves the product price from the Products table into the Sales table.

### Real-World Application
RELATED() helps combine information from different tables without manually looking up matching values.

---

## 5. Filter Context in Power BI

### Definition
Filter context refers to the filters applied to data before a DAX calculation is evaluated.

It determines which data is considered during a calculation.

### Example

Consider the following sales data:

| Region | Sales |
|---|---:|
| North | 20,000 |
| South | 30,000 |
| East | 15,000 |
| West | 25,000 |

If we select South using a slicer, Power BI displays only South region sales.

**Result:** 30,000

This happens because the slicer creates a filter context.

### Importance of Filter Context
- Helps create interactive reports.
- Allows calculations based on user selections.
- Makes dashboards dynamic.
- Helps analyze business performance by category, region, and date.

---

## 6. Difference Between DAX Functions

| Function | Purpose |
|---|---|
| CALCULATE() | Evaluates an expression with modified filter context |
| FILTER() | Returns rows that satisfy a condition |
| ALL() | Removes filters from a table or column |
| RELATED() | Retrieves values from a related table |

---

## 7. Practical Applications in Data Analysis

These DAX functions are useful in real-world business scenarios:

1. **Regional Sales Analysis:** Calculate sales for individual regions using CALCULATE().
2. **High-Value Transactions:** Identify transactions above a specific amount using FILTER().
3. **Overall Sales Comparison:** Compare filtered sales against overall sales using ALL().
4. **Data Model Analysis:** Retrieve product details from related tables using RELATED().
5. **Interactive Dashboards:** Use filter context to make reports respond to slicers and selections.

---

## 8. Key Learnings

Today, I learned:

- What DAX is and why it is important in Power BI.
- How CALCULATE() modifies filter context.
- How FILTER() returns rows based on conditions.
- How ALL() removes filters.
- How RELATED() retrieves values from related tables.
- What filter context means and how it works.
- How DAX functions are used in real-world business analysis.

## 9. Conclusion

DAX functions play an important role in Power BI because they help Data Analysts perform advanced calculations and analyze business data.

Understanding CALCULATE(), FILTER(), ALL(), and RELATED() builds a strong foundation for creating meaningful reports and interactive dashboards.

**Day 38 successfully completed!**

---

**#DataAnalytics #PowerBI #DAX #DataAnalysis #Day38 #60DaysDataAnalystChallenge**