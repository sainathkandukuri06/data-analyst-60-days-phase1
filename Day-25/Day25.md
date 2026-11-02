# Day 25 – SQL Window Functions

# Learning Objectives

- Understand SQL Window Functions.
- Learn the `OVER()` clause.
- Understand `PARTITION BY` and `ORDER BY`.
- Practise `ROW_NUMBER()`, `RANK()`, and `DENSE_RANK()`.
- Understand `LAG()` and `LEAD()`.
- Perform aggregate calculations using window functions.
- Calculate running totals and moving averages.
- Solve real-world analytical problems using SQL.

---

## 1. What Are Window Functions?

Window functions perform calculations across multiple rows while preserving the original rows in the result.

Unlike `GROUP BY`, window functions do not reduce the number of rows.

### Example

```sql
SELECT
    Name,
    Department,
    Salary,
    AVG(Salary) OVER(
        PARTITION BY Department
    ) AS Department_Average
FROM Employees;
```

**Key Points:**

- Preserves individual employee records.
- Calculates department-wise averages.
- Performs analytical calculations across related rows.

## 2. Components of Window Functions

### A. OVER()

Defines the window of rows used for calculation.

```sql
SELECT
    Name,
    Salary,
    AVG(Salary) OVER() AS Average_Salary
FROM Employees;
```

### B. PARTITION BY

Divides records into logical groups without combining rows.

```sql
SELECT
    Name,
    Department,
    Salary,
    AVG(Salary) OVER(
        PARTITION BY Department
    ) AS Department_Average
FROM Employees;
```

### C. ORDER BY

Defines the order in which rows are considered inside the window.

```sql
SELECT
    Name,
    Salary,
    ROW_NUMBER() OVER(
        ORDER BY Salary DESC
    ) AS Row_Number
FROM Employees;
```

---

## 3. ROW_NUMBER()

Assigns a unique sequential number to each row.

```sql
SELECT
    Name,
    Department,
    Salary,
    ROW_NUMBER() OVER(
        PARTITION BY Department
        ORDER BY Salary DESC
    ) AS Row_Num
FROM Employees;
```

**Uses:**
- Identifying duplicate records.
- Finding the latest transactions.
- Ranking employees.
- Selecting the top records.

## 4. RANK()

Assigns rankings based on values. Duplicate values receive the same rank, and subsequent ranks are skipped.

```sql
SELECT
    Name,
    Salary,
    RANK() OVER(
        ORDER BY Salary DESC
    ) AS Salary_Rank
FROM Employees;
```

Example ranking:

| Salary | Rank |
|---:|---:|
| 80000 | 1 |
| 70000 | 2 |
| 70000 | 2 |
| 60000 | 4 |

## 5. DENSE_RANK()

Assigns rankings based on values without skipping ranking numbers.

```sql
SELECT
    Name,
    Salary,
    DENSE_RANK() OVER(
        ORDER BY Salary DESC
    ) AS Dense_Rank
FROM Employees;
```

Example ranking:

| Salary | Dense Rank |
|---:|---:|
| 80000 | 1 |
| 70000 | 2 |
| 70000 | 2 |
| 60000 | 3 |

### Difference Between Ranking Functions

| Function | Description |
|---|---|
| ROW_NUMBER() | Unique sequential numbering |
| RANK() | Same rank for ties, skips subsequent ranks |
| DENSE_RANK() | Same rank for ties, does not skip ranks |

---

## 6. LAG() Function

Retrieves a value from a previous row without using a self-join.

```sql
SELECT
    Month,
    Sales,
    LAG(Sales) OVER(
        ORDER BY Month_Number
    ) AS Previous_Month_Sales
FROM Monthly_Sales;
```

**Uses:**
- Comparing monthly sales.
- Analysing previous transactions.
- Calculating revenue growth.
- Identifying changes in customer behaviour.

### Month-over-Month Growth Formula

```text
Growth = Current Sales - Previous Sales

Growth Percentage =
((Current Sales - Previous Sales) / Previous Sales) * 100
```

---

## 7. LEAD() Function

Retrieves a value from a future row.

```sql
SELECT
    Month,
    Sales,
    LEAD(Sales) OVER(
        ORDER BY Month_Number
    ) AS Next_Month_Sales
FROM Monthly_Sales;
```

**Difference:**
- LAG() retrieves previous row values.
- LEAD() retrieves next row values.

---

## 8. Aggregate Window Functions

Aggregate functions can also be used with the OVER() clause.

### SUM() OVER()

Calculates the total across a window.

```sql
SELECT
    Name,
    Department,
    Salary,
    SUM(Salary) OVER(
        PARTITION BY Department
    ) AS Department_Total
FROM Employees;
```

### AVG() OVER()

Calculates the average across a window.

```sql
SELECT
    Name,
    Department,
    Salary,
    AVG(Salary) OVER(
        PARTITION BY Department
    ) AS Average_Salary
FROM Employees;
```

### COUNT() OVER()

Counts the number of rows in a window.

```sql
SELECT
    Name,
    Department,
    COUNT(*) OVER(
        PARTITION BY Department
    ) AS Employee_Count
FROM Employees;
```

### MIN() and MAX() OVER()

Finds the minimum and maximum values within a window.

```sql
SELECT
    Name,
    Department,
    Salary,
    MIN(Salary) OVER(
        PARTITION BY Department
    ) AS Minimum_Salary,
    MAX(Salary) OVER(
        PARTITION BY Department
    ) AS Maximum_Salary
FROM Employees;
```

---

## 9. Running Total

A running total calculates the cumulative sum of values from the first row to the current row.

```sql
SELECT
    Day,
    Sales,
    SUM(Sales) OVER(
        ORDER BY Day_Number
        ROWS BETWEEN UNBOUNDED PRECEDING
        AND CURRENT ROW
    ) AS Running_Total
FROM Daily_Sales;
```

### Window Frame Explanation

| Keyword | Meaning |
|---|---|
| ROWS | Defines a row-based window frame |
| UNBOUNDED PRECEDING | Starts from the first row |
| CURRENT ROW | Ends at the current row |

**Real-world applications:**
- Cumulative revenue.
- Daily sales reports.
- Monthly expense tracking.
- Business performance analysis.

---

## 10. Moving Average

A moving average calculates the average of a specified number of recent rows.

```sql
SELECT
    Day,
    Sales,
    AVG(Sales) OVER(
        ORDER BY Day_Number
        ROWS BETWEEN 2 PRECEDING
        AND CURRENT ROW
    ) AS Moving_Average
FROM Daily_Sales;
```

**Applications:**
- Sales trend analysis.
- Website traffic analysis.
- Financial data analysis.
- Identifying business trends.

---

## 11. Real-World SQL Problem

### Find the Top 2 Highest-Paid Employees in Each Department

```sql
WITH RankedEmployees AS (
    SELECT
        Employee_ID,
        Name,
        Department,
        Salary,
        DENSE_RANK() OVER(
            PARTITION BY Department
            ORDER BY Salary DESC
        ) AS Salary_Rank
    FROM Employees
)
SELECT *
FROM RankedEmployees
WHERE Salary_Rank <= 2;
```

**Explanation:**

1. PARTITION BY separates employees by department.
2. ORDER BY sorts employees by salary.
3. DENSE_RANK() assigns salary rankings.
4. The outer query selects employees ranked in the top two positions.

Note: DENSE_RANK() can return more than two employees when salaries are tied.

---

## 12. Window Functions vs GROUP BY

| Feature | GROUP BY | Window Functions |
|---|---|---|
| Purpose | Aggregate records | Analytical calculations |
| Preserves individual rows | No | Yes |
| Ranking | Not directly supported | Supported |
| Running totals | Not directly supported | Supported |
| Previous-row comparison | Not directly supported | Supported |

---

## 13. SQL Logical Execution Order

Understanding SQL execution order helps explain why window functions cannot normally be filtered directly in the WHERE clause.

Simplified logical processing order:

1. FROM
2. JOIN
3. WHERE
4. GROUP BY
5. HAVING
6. SELECT (including window expressions)
7. ORDER BY
8. LIMIT / OFFSET

### Filtering Window Functions Using CTE

```sql
WITH Ranked AS (
    SELECT
        Name,
        Salary,
        ROW_NUMBER() OVER(
            ORDER BY Salary DESC
        ) AS rn
    FROM Employees
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

## 14. Practical SQL Exercises

### Beginner Level

1. Display all employees with a row number.
2. Assign row numbers department-wise.
3. Rank employees based on salary.
4. Find the highest salary in each department.
5. Calculate department-wise average salaries.

### Intermediate Level

6. Find the top 2 highest-paid employees in each department.
7. Compare employee salaries with previous employees.
8. Display the next employee's salary using LEAD().
9. Calculate department-wise total salaries.
10. Count employees in each department.

### Advanced Level

11. Find the second-highest salary in each department.
12. Identify employees earning more than their department's average.
13. Calculate department-wise running totals.
14. Identify employees receiving identical salaries.
15. Generate a report using ROW_NUMBER(), RANK(), and DENSE_RANK().

---

## 15. SQL Interview Questions

1. What are SQL Window Functions?
2. What is the difference between GROUP BY and PARTITION BY?
3. What is the purpose of OVER()?
4. Explain ROW_NUMBER(), RANK(), and DENSE_RANK().
5. What is the difference between LAG() and LEAD()?
6. Can aggregate functions be used with window functions?
7. What is a running total?
8. What is a moving average?
9. Why can't window functions be used directly in WHERE?
10. How do you find the top 3 employees in every department?
11. What is a window frame?
12. What happens when two employees have identical salaries while using RANK()?

---

## 16. Key Takeaways

Today I learned:

- SQL Window Functions.
- OVER(), PARTITION BY, and ORDER BY.
- ROW_NUMBER(), RANK(), and DENSE_RANK().
- LAG() and LEAD().
- Aggregate Window Functions.
- Running Totals.
- Moving Averages.
- Window Frames.
- Real-world SQL analytical problems.

# Real-World Applications

Window functions are frequently used in:

- Business Intelligence.
- Sales and Revenue Analysis.
- Financial Reporting.
- Customer Behaviour Analysis.
- Employee Performance Analysis.
- E-commerce Analytics.
- Data Cleaning and Duplicate Identification.