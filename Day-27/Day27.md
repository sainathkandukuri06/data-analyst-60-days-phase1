# Day 27 - SQL Interview Practice: Real-World SQL Problems & Advanced Queries

# Learning Objectives

- Understand and implement different types of SQL JOINs.
- Solve SQL problems using Subqueries.
- Understand Correlated Subqueries.
- Apply Window Functions for ranking and analytical calculations.
- Calculate Running Totals using window functions.
- Perform date-based analysis.
- Clean and transform text using String Functions.
- Combine multiple SQL concepts to solve business problems.
- Practice commonly asked SQL interview questions.

## 1. SQL JOINs

JOINs are used to retrieve and combine related information from multiple database tables.

### INNER JOIN

Returns only matching records from both tables.

```sql
SELECT
    C.CustomerName,
    O.OrderID,
    O.Amount
FROM Customers C
INNER JOIN Orders O
    ON C.CustomerID = O.CustomerID;
```

### LEFT JOIN

Returns all records from the left table and matching records from the right table.

```sql
SELECT
    C.CustomerName,
    O.OrderID
FROM Customers C
LEFT JOIN Orders O
    ON C.CustomerID = O.CustomerID;
```

### Find Customers Without Orders

```sql
SELECT
    C.CustomerID,
    C.CustomerName
FROM Customers C
LEFT JOIN Orders O
    ON C.CustomerID = O.CustomerID
WHERE O.OrderID IS NULL;
```

**Business Application:** Identifying customers who registered but never purchased anything.

---

## 2. Aggregate Functions with JOINs

Aggregate functions perform calculations on multiple records.

Important functions:

- SUM() - Calculates the total.
- AVG() - Calculates the average.
- COUNT() - Counts records.
- MAX() - Finds the maximum value.
- MIN() - Finds the minimum value.

### Calculate Total Spending by Each Customer

```sql
SELECT
    C.CustomerName,
    SUM(O.Amount) AS TotalSpent
FROM Customers C
INNER JOIN Orders O
    ON C.CustomerID = O.CustomerID
GROUP BY C.CustomerName
ORDER BY TotalSpent DESC;
```

**Business Application:** Identifying high-value customers based on their total spending.

## 3. SQL Subqueries

A Subquery is a query written inside another SQL query.

### Find Employees Earning More Than Average Salary

```sql
SELECT
    EmployeeName,
    Salary
FROM Employees
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
);
```

### Find the Second-Highest Salary

```sql
SELECT MAX(Salary) AS SecondHighestSalary
FROM Employees
WHERE Salary < (
    SELECT MAX(Salary)
    FROM Employees
);
```

### Correlated Subquery

A correlated subquery depends on values from the outer query.

Find employees earning more than their department's average salary.

```sql
SELECT
    E.EmployeeName,
    E.Department,
    E.Salary
FROM Employees E
WHERE E.Salary > (
    SELECT AVG(E2.Salary)
    FROM Employees E2
    WHERE E2.Department = E.Department
);
```

**Business Application:** Comparing employee salaries against department-level averages.

---

## 4. SQL Window Functions

Window Functions perform calculations across related rows without grouping the result into a single row.

Important Window Functions:

| Function | Description |
|---|---|
| ROW_NUMBER() | Assigns a unique sequential number. |
| RANK() | Assigns ranks with gaps after ties. |
| DENSE_RANK() | Assigns ranks without gaps after ties. |
| SUM() OVER() | Calculates window-based totals. |
| AVG() OVER() | Calculates window-based averages. |

### Rank Employees Based on Salary

```sql
SELECT
    EmployeeName,
    Salary,
    RANK() OVER (
        ORDER BY Salary DESC
    ) AS SalaryRank
FROM Employees;
```

### Find Top 2 Employees in Each Department

```sql
WITH EmployeeRanking AS (
    SELECT
        EmployeeName,
        Department,
        Salary,
        ROW_NUMBER() OVER (
            PARTITION BY Department
            ORDER BY Salary DESC
        ) AS RowNum
    FROM Employees
)
SELECT *
FROM EmployeeRanking
WHERE RowNum <= 2;
```

### Calculate Running Total of Sales

```sql
SELECT
    OrderID,
    OrderDate,
    Amount,
    SUM(Amount) OVER (
        ORDER BY OrderDate, OrderID
        ROWS BETWEEN UNBOUNDED PRECEDING
        AND CURRENT ROW
    ) AS RunningTotal
FROM Orders;
```

**Business Application:** Employee rankings, cumulative revenue reports, and department-wise performance analysis.

---

## 5. SQL Date Functions

Date Functions help analyze time-based business information.

Important functions:

| Function | Description |
|---|---|
| YEAR() | Extracts the year. |
| MONTH() | Extracts the month. |
| DAY() | Extracts the day. |
| DATEDIFF() | Calculates the difference between dates. |
| DATEADD() | Adds or subtracts a date interval. |
| GETDATE() | Returns the current system date and time in SQL Server. |

### Find Orders Placed in February 2026

```sql
SELECT *
FROM Orders
WHERE OrderDate >= '2026-02-01'
AND OrderDate < '2026-03-01';
```

### Calculate Monthly Revenue

```sql
SELECT
    YEAR(OrderDate) AS OrderYear,
    MONTH(OrderDate) AS OrderMonth,
    SUM(Amount) AS MonthlyRevenue
FROM Orders
GROUP BY
    YEAR(OrderDate),
    MONTH(OrderDate)
ORDER BY
    OrderYear,
    OrderMonth;
```

### Find Customers Who Have Not Purchased in the Last 90 Days

```sql
SELECT
    C.CustomerName,
    MAX(O.OrderDate) AS LastOrderDate
FROM Customers C
INNER JOIN Orders O
    ON C.CustomerID = O.CustomerID
GROUP BY
    C.CustomerID,
    C.CustomerName
HAVING MAX(O.OrderDate) <
    DATEADD(DAY, -90, GETDATE());
```

**Business Application:** Monthly revenue analysis, customer retention analysis, and purchase behavior tracking.

---

## 6. SQL String Functions

String Functions help clean, manipulate, and transform text data.

Important functions:

| Function | Description |
|---|---|
| UPPER() | Converts text into uppercase. |
| LOWER() | Converts text into lowercase. |
| TRIM() | Removes leading and trailing spaces. |
| LEFT() | Extracts characters from the left. |
| RIGHT() | Extracts characters from the right. |
| LEN() | Returns the length of a string in SQL Server. |
| SUBSTRING() | Extracts a portion of a string. |

### Convert Customer Names to Uppercase

```sql
SELECT
    CustomerName,
    UPPER(CustomerName) AS UppercaseName
FROM Customers;
```

### Remove Unwanted Spaces

```sql
SELECT
    TRIM(CustomerName) AS CleanName
FROM Customers;
```

### Extract First Three Characters

```sql
SELECT
    CustomerName,
    LEFT(CustomerName, 3) AS ShortName
FROM Customers;
```

**Business Application:** Data cleaning, text standardization, and customer information processing.

---

## 7. Combining Multiple SQL Concepts

### Real-World Business Problem: Customer Revenue Analysis

Requirement:

Generate a report containing:

- Customer Name
- Total Number of Orders
- Total Spending
- Latest Order Date

Display only customers whose total spending is greater than ₹5,000.

```sql
SELECT
    C.CustomerName,
    COUNT(O.OrderID) AS TotalOrders,
    SUM(O.Amount) AS TotalSpending,
    MAX(O.OrderDate) AS LastOrderDate
FROM Customers C
INNER JOIN Orders O
    ON C.CustomerID = O.CustomerID
GROUP BY
    C.CustomerID,
    C.CustomerName
HAVING SUM(O.Amount) > 5000
ORDER BY TotalSpending DESC;
```

### Concepts Used

1. INNER JOIN - Combines customer and order information.
2. COUNT() - Counts customer orders.
3. SUM() - Calculates total spending.
4. MAX() - Finds the latest order date.
5. GROUP BY - Groups records by customer.
6. HAVING - Filters customers based on total spending.
7. ORDER BY - Sorts the results.

## 8. SQL Interview Questions Practiced

| No. | Interview Question | SQL Concept |
|---|---|---|
| 1 | Find the highest salary. | MAX() |
| 2 | Find the second-highest salary. | Subquery |
| 3 | Find the third-highest salary. | DENSE_RANK() |
| 4 | Find employees earning above average. | Subquery |
| 5 | Find employees in each department. | GROUP BY |
| 6 | Find departments with more than two employees. | HAVING |
| 7 | Find customers without orders. | LEFT JOIN |
| 8 | Find total revenue by customer. | JOIN + SUM() |
| 9 | Find top three products by quantity sold. | JOIN + GROUP BY |
| 10 | Find top two salaries per department. | ROW_NUMBER() |
| 11 | Find duplicate customer names. | GROUP BY + HAVING |
| 12 | Find monthly revenue. | Date Functions |
| 13 | Calculate cumulative revenue. | Window Functions |
| 14 | Find customers' latest orders. | MAX() |
| 15 | Clean customer names. | String Functions |

---

## 9. Key Learnings

Through today's practice, I learned:

- How to solve business problems using SQL JOINs.
- How to use Subqueries to solve complex analytical problems.
- How Correlated Subqueries work.
- How Window Functions simplify analytical calculations.
- How to calculate employee rankings and running totals.
- How to perform monthly revenue analysis.
- How to clean and standardize text data.
- How to combine multiple SQL concepts in one query.
- How SQL supports real-world business decision-making.

---

## 10. Tools & Technologies

- SQL Server
- SQL Server Management Studio (SSMS)
- SQL Queries
- Relational Database Concepts

