# Day 24 - SQL Subqueries (Nested Queries)

Subqueries are also known as:
- Nested Queries
- Inner Queries

# Learning Objectives

- Understand SQL Subqueries.
- Learn different types of subqueries.
- Understand single-row and multiple-row subqueries.
- Learn correlated and scalar subqueries.
- Work with IN, NOT IN, EXISTS, NOT EXISTS, ANY, and ALL operators.
- Use subqueries inside WHERE, SELECT, FROM, and HAVING clauses.
- Understand real-world applications of subqueries.
- Learn basic SQL query performance optimization.

## 1. What is a Subquery?

A Subquery is a query placed inside another SQL query.

**Example: Find employees earning more than the average salary.**

```sql
SELECT *
FROM Employees
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
);
```

### How It Works

1. The inner query calculates the average salary.
2. The outer query receives the calculated result.
3. SQL compares employee salaries against the average.
4. Employees earning above average are returned.

---

## 2. Types of SQL Subqueries

### 2.1 Single-Row Subquery

Returns only one row from the inner query.

```sql
SELECT *
FROM Employees
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
);
```

Common operators:
- =
- >
- <
- >=
- <=
- <>

### 2.2 Multiple-Row Subquery

Returns multiple rows from the inner query.

```sql
SELECT *
FROM Employees
WHERE Department IN (
    SELECT Department
    FROM Employees
    WHERE Salary > 60000
);
```

### 2.3 Multiple-Column Subquery

Returns multiple columns from the inner query.

```sql
SELECT *
FROM Employees
WHERE (Department, Salary) IN (
    SELECT Department, Salary
    FROM Employees
    WHERE Name = 'Kiran'
);
```

### 2.4 Scalar Subquery

Returns exactly one row and one column.

```sql
SELECT
    Name,
    Salary,
    (SELECT AVG(Salary)
     FROM Employees) AS Average_Salary
FROM Employees;
```

### 2.5 Correlated Subquery

A correlated subquery depends on the outer query and references its columns.

**Example: Find employees earning more than their department's average salary.**

```sql
SELECT
    E1.Name,
    E1.Department,
    E1.Salary
FROM Employees E1
WHERE E1.Salary > (
    SELECT AVG(E2.Salary)
    FROM Employees E2
    WHERE E2.Department = E1.Department
);
```

---

## 3. Important SQL Operators

### IN Operator

Checks whether a value matches any value in a list.

```sql
SELECT *
FROM Employees
WHERE Department IN (
    SELECT Department
    FROM Employees
    WHERE Salary > 60000
);
```

### NOT IN Operator

Returns records that do not match the values returned by the subquery.

```sql
SELECT *
FROM Employees
WHERE Department NOT IN (
    SELECT Department
    FROM Employees
    WHERE Salary > 60000
);
```

**Note:** Be careful when the subquery returns NULL values.

### EXISTS Operator

Checks whether the subquery returns at least one record.

```sql
SELECT *
FROM Customers C
WHERE EXISTS (
    SELECT 1
    FROM Orders O
    WHERE O.Customer_ID = C.Customer_ID
);
```

### NOT EXISTS Operator

Checks whether no matching records exist.

```sql
SELECT *
FROM Customers C
WHERE NOT EXISTS (
    SELECT 1
    FROM Orders O
    WHERE O.Customer_ID = C.Customer_ID
);
```

### ANY Operator

Returns records when the comparison is true for at least one value returned by the subquery.

```sql
SELECT *
FROM Employees
WHERE Salary > ANY (
    SELECT Salary
    FROM Employees
    WHERE Department = 'HR'
);
```

### ALL Operator

Returns records when the comparison is true for every value returned by the subquery.

```sql
SELECT *
FROM Employees
WHERE Salary > ALL (
    SELECT Salary
    FROM Employees
    WHERE Department = 'HR'
);
```

---

## 4. Subqueries in Different SQL Clauses

### Subquery in WHERE

Used to filter records.

```sql
SELECT *
FROM Employees
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
);
```

### Subquery in SELECT

Used to display calculated values alongside existing columns.

```sql
SELECT
    Name,
    Salary,
    (SELECT MAX(Salary)
     FROM Employees) AS Highest_Salary
FROM Employees;
```

### Subquery in FROM

A subquery in FROM creates a derived table.

```sql
SELECT *
FROM (
    SELECT
        Department,
        AVG(Salary) AS Avg_Salary
    FROM Employees
    GROUP BY Department
) AS Dept_Summary
WHERE Avg_Salary > 40000;
```

### Subquery in HAVING

Used to filter grouped results.

```sql
SELECT
    Department,
    AVG(Salary) AS Avg_Salary
FROM Employees
GROUP BY Department
HAVING AVG(Salary) > (
    SELECT AVG(Salary)
    FROM Employees
);
```

---

## 5. Subquery vs JOIN vs CTE

| Feature | Subquery | JOIN | CTE |
|---|---|---|---|
| Purpose | Nested query | Combines tables | Organizes queries |
| Usage | Filtering and calculations | Table relationships | Complex analysis |
| Readability | Depends on complexity | Generally clear | Often easier to read |
| Keyword | SELECT | JOIN | WITH |

### Example of CTE

```sql
WITH Department_Salary AS (
    SELECT
        Department,
        AVG(Salary) AS Avg_Salary
    FROM Employees
    GROUP BY Department
)
SELECT *
FROM Department_Salary
WHERE Avg_Salary > 40000;
```

---

## 6. SQL Performance Optimization

Important practices when working with subqueries:

1. Avoid unnecessary correlated subqueries.
2. Use appropriate indexes.
3. Avoid SELECT * when unnecessary.
4. Use EXISTS for existence checks.
5. Analyze query execution plans using EXPLAIN.
6. Compare subqueries with JOINs and CTEs when optimizing complex queries.

Example:

```sql
EXPLAIN
SELECT *
FROM Employees
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
);
```

---

## 7. Real-World Applications

SQL Subqueries are useful in real-world business analysis.

| Business Requirement | SQL Concept |
|---|---|
| Employees earning above average | Single-row Subquery |
| Employees in selected departments | IN |
| Customers who placed orders | EXISTS |
| Customers without orders | NOT EXISTS |
| Employees above department average | Correlated Subquery |
| Departments above company average | HAVING Subquery |
| Products priced above all competitor prices | ALL |
| Products priced above at least one competitor price | ANY |

---

## 8. Key Learnings

After completing Day 24, I understood:

- How SQL Subqueries work.
- Difference between inner and outer queries.
- Different types of subqueries.
- How correlated subqueries work.
- Difference between IN and EXISTS.
- Difference between ANY and ALL.
- How to use subqueries in different SQL clauses.
- Difference between Subqueries, JOINs, and CTEs.
- Basic SQL performance optimization.

---

## 9. Practice Questions

1. Find employees whose salary is greater than the overall average salary.
2. Find the employee earning the highest salary.
3. Find employees working in departments where at least one employee earns more than 60000.
4. Find employees earning more than their department's average salary.
5. Find customers who have placed at least one order.
6. Find customers who have never placed an order.
7. Find departments whose average salary is greater than the overall average salary.
8. Find employees whose salary is greater than every employee in the HR department.
9. Find the second-highest distinct salary using a subquery.
10. Find customers whose total order amount is greater than the average total order amount per customer.