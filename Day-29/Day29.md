# Day 29 – SQL Window Functions

## 📌 Introduction

SQL Window Functions are advanced SQL functions used to perform calculations across a set of related rows without combining individual rows into a single result.

They help Data Analysts perform complex calculations such as:
- Ranking employees based on salary.
- Calculating department-wise totals.
- Finding previous and next records.
- Calculating running totals.
- Comparing monthly revenue.
- Identifying duplicate records.

**Main Advantage:** Window Functions preserve individual rows while performing calculations across multiple rows.

---

## 1. GROUP BY vs Window Functions

### GROUP BY
GROUP BY combines rows with the same values into summary records.

Example:

```sql
SELECT
    Department,
    SUM(Sales) AS Total_Sales
FROM Sales
GROUP BY Department;
```

### Window Functions
Window Functions calculate values across related rows without removing individual records.

Example:

```sql
SELECT
    Employee,
    Department,
    Sales,
    SUM(Sales) OVER(
        PARTITION BY Department
    ) AS Department_Total
FROM Sales;
```

### Differences

| GROUP BY | Window Functions |
|---|---|
| Combines multiple rows | Preserves individual rows |
| Returns summarized results | Returns detailed results |
| Reduces row count | Maintains row count |
| Used for aggregation | Used for advanced analysis |

---

## 2. OVER() Clause

The OVER() clause defines the set of rows used by a Window Function.

**Syntax:**

```sql
FUNCTION_NAME() OVER()
```

**Example:**

```sql
SELECT
    Employee,
    Sales,
    SUM(Sales) OVER() AS Total_Sales
FROM Sales;
```

**Explanation:**

- SQL calculates total sales across all records.
- The total is displayed alongside every employee.
- Individual employee records remain unchanged.

**Use Case:** Displaying company-wide totals alongside individual sales records.

---

## 3. PARTITION BY

PARTITION BY divides data into logical groups for separate calculations.

Unlike GROUP BY, it does not combine individual records.

**Syntax:**

```sql
FUNCTION_NAME() OVER(
    PARTITION BY Column_Name
)
```

**Example:**

```sql
SELECT
    Employee,
    Department,
    Salary,
    AVG(Salary) OVER(
        PARTITION BY Department
    ) AS Department_Average
FROM Employees;
```

**Explanation:**

- Employees are divided by department.
- SQL calculates the average salary for each department.
- Every employee record displays its department average.

**Use Case:** Comparing individual employee salaries with department averages.

---

## 4. ORDER BY in Window Functions

ORDER BY specifies the order in which rows are considered within a window.

**Example:**

```sql
SELECT
    Employee,
    Sales,
    SUM(Sales) OVER(
        ORDER BY Order_ID
    ) AS Running_Total
FROM Sales;
```

**Explanation:**

The running total increases as SQL processes each row in the specified order.

For example:

| Sales | Running Total |
|---:|---:|
| 5000 | 5000 |
| 7000 | 12000 |
| 3000 | 15000 |
| 6000 | 21000 |

**Use Case:** Calculating cumulative revenue and monthly business performance.

---

## 5. ROW_NUMBER()

ROW_NUMBER() assigns a unique sequential number to every row within a window.

**Syntax:**

```sql
ROW_NUMBER() OVER(
    PARTITION BY Column_Name
    ORDER BY Column_Name
)
```

**Example:**

```sql
SELECT
    Employee,
    Department,
    Salary,
    ROW_NUMBER() OVER(
        PARTITION BY Department
        ORDER BY Salary DESC
    ) AS Row_Num
FROM Employees;
```

**Explanation:**

1. Employees are divided by department.
2. Employees are sorted by salary in descending order.
3. Each employee receives a unique sequential number.

**Use Case:**
- Finding the latest order for each customer.
- Identifying duplicate records.
- Selecting the highest-paid employee in each department.

---

## 6. RANK()

RANK() assigns ranking numbers based on values.

When multiple rows have the same value, they receive the same rank. The next rank is skipped.

**Example:**

```sql
SELECT
    Employee,
    Salary,
    RANK() OVER(
        ORDER BY Salary DESC
    ) AS Employee_Rank
FROM Employees;
```

**Example Output:**

| Salary | Rank |
|---:|---:|
| 90000 | 1 |
| 80000 | 2 |
| 80000 | 2 |
| 60000 | 4 |

**Use Case:** Ranking employees based on performance or salary.

---

## 7. DENSE_RANK()

DENSE_RANK() assigns rankings without skipping numbers after tied values.

**Example:**

```sql
SELECT
    Employee,
    Salary,
    DENSE_RANK() OVER(
        ORDER BY Salary DESC
    ) AS Salary_Rank
FROM Employees;
```

**Example Output:**

| Salary | Dense Rank |
|---:|---:|
| 90000 | 1 |
| 80000 | 2 |
| 80000 | 2 |
| 60000 | 3 |

**Use Case:** Finding the second-highest distinct salary.

### Difference Between Ranking Functions

| Function | Behaviour |
|---|---|
| ROW_NUMBER() | Always assigns unique numbers |
| RANK() | Same rank for ties, skips subsequent ranks |
| DENSE_RANK() | Same rank for ties, does not skip ranks |

---

## 8. Aggregate Window Functions

Aggregate functions can be used with OVER() to perform calculations without grouping away individual records.

### SUM()
Calculates the total value.

```sql
SELECT
    Employee,
    Salary,
    SUM(Salary) OVER() AS Total_Salary
FROM Employees;
```

### AVG()
Calculates the average value.

```sql
SELECT
    Employee,
    Salary,
    AVG(Salary) OVER() AS Average_Salary
FROM Employees;
```

### COUNT()
Counts records in a window.

```sql
SELECT
    Employee,
    Department,
    COUNT(*) OVER(
        PARTITION BY Department
    ) AS Employee_Count
FROM Employees;
```

### MIN() and MAX()

```sql
SELECT
    Employee,
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

**Use Case:** Department-wise salary analysis and employee performance reporting.

---

## 9. LAG() Function

LAG() retrieves a value from a previous row without using a self-join.

**Syntax:**

```sql
LAG(Column_Name, Offset, Default_Value)
OVER(ORDER BY Column_Name)
```

**Example:**

```sql
SELECT
    Month,
    Revenue,
    LAG(Revenue) OVER(
        ORDER BY Month_Number
    ) AS Previous_Revenue
FROM Monthly_Sales;
```

**Explanation:**

- LAG() retrieves the previous month's revenue.
- The first row returns NULL when no previous row exists.
- Offset determines how many rows backward SQL looks.

**Use Case:** Comparing current-month revenue with previous-month revenue.

### Month-over-Month Growth Formula

```sql
(Current_Revenue - Previous_Revenue)
* 100.0 / Previous_Revenue
```

This helps identify revenue growth and decline.

---

## 10. LEAD() Function

LEAD() retrieves a value from a following row.

It is the opposite of LAG().

**Syntax:**

```sql
LEAD(Column_Name, Offset, Default_Value)
OVER(ORDER BY Column_Name)
```

**Example:**

```sql
SELECT
    Month,
    Revenue,
    LEAD(Revenue) OVER(
        ORDER BY Month_Number
    ) AS Next_Month_Revenue
FROM Monthly_Sales;
```

**Explanation:**

- Retrieves the next month's revenue.
- The final row returns NULL if no following row exists.
- Offset determines how many rows forward SQL looks.

**Use Case:** Comparing current values with future scheduled values.

### Difference Between LAG() and LEAD()

| LAG() | LEAD() |
|---|---|
| Looks backward | Looks forward |
| Retrieves previous row | Retrieves next row |
| Used for historical comparisons | Used for forward comparisons |

---

## 11. Window Frames – ROWS BETWEEN

Window Frames specify which rows should be included in a calculation relative to the current row.

They are useful for moving averages and cumulative calculations.

**Example:**

```sql
SELECT
    Month,
    Revenue,
    AVG(Revenue) OVER(
        ORDER BY Month_Number
        ROWS BETWEEN 2 PRECEDING
        AND CURRENT ROW
    ) AS Moving_Average
FROM Monthly_Sales;
```

**Explanation:**

- 2 PRECEDING: Includes two previous rows.
- CURRENT ROW: Includes the current row.
- AVG(): Calculates the average of those rows.

This example calculates a three-row moving average when at least three rows are available.

### Important Frame Keywords

| Keyword | Meaning |
|---|---|
| UNBOUNDED PRECEDING | Starts from the first row |
| 1 PRECEDING | One previous row |
| 2 PRECEDING | Two previous rows |
| CURRENT ROW | Current row |
| 1 FOLLOWING | One following row |
| UNBOUNDED FOLLOWING | Extends to the last row |

**Use Case:** Analysing monthly revenue trends and smoothing fluctuations.

## 12. Practical Business Applications

Window Functions are commonly used in real-world Data Analyst projects.

| Business Problem | SQL Function |
|---|---|
| Find highest-paid employees | ROW_NUMBER() |
| Find second-highest salary | DENSE_RANK() |
| Rank employee performance | RANK() |
| Calculate department averages | AVG() OVER() |
| Calculate cumulative revenue | SUM() OVER() |
| Compare monthly revenue | LAG() |
| Compare with next month's revenue | LEAD() |
| Identify duplicate records | ROW_NUMBER() |
| Calculate moving averages | AVG() with ROWS BETWEEN |

## 13. Important SQL Concepts Learned

1. Understanding Window Functions and their purpose.
2. Difference between GROUP BY and Window Functions.
3. Understanding OVER(), PARTITION BY, and ORDER BY.
4. Assigning rankings using ROW_NUMBER(), RANK(), and DENSE_RANK().
5. Performing aggregate calculations using Window Functions.
6. Comparing previous and next records using LAG() and LEAD().
7. Calculating running totals and moving averages using Window Frames.
8. Solving real-world business problems using SQL.

## 14. Practice Questions

1. Find the average salary of all employees.
2. Calculate department-wise total salaries.
3. Assign row numbers to employees based on salary.
4. Rank employees using RANK().
5. Find the second-highest distinct salary.
6. Find the highest-paid employee in each department.
7. Identify employees earning above their department average.
8. Calculate each employee's percentage contribution to total salary.
9. Find the top two employees in each department.
10. Calculate a running total of employee salaries.