# Day 28 - SQL Common Table Expressions (CTEs) and Views

# Learning Objectives

- Understand Common Table Expressions (CTEs).
- Learn how to use the `WITH` keyword.
- Write CTEs with aggregate functions.
- Use CTEs with `GROUP BY` and `HAVING`.
- Understand multiple CTEs in a single query.
- Combine CTEs with JOIN operations.
- Understand Recursive CTEs.
- Learn SQL Views and their applications.
- Understand the differences between CTEs, Subqueries, and Views.

---

## 1. Common Table Expressions (CTEs)

A Common Table Expression (CTE) is a temporary named result set created using the `WITH` keyword.

CTEs help divide complex SQL queries into smaller and more understandable steps.

### Syntax

```sql
WITH cte_name AS (
    SELECT column1, column2
    FROM table_name
    WHERE condition
)
SELECT *
FROM cte_name;
```

### Example

Find employees whose salary is greater than 45,000.

```sql
WITH HighSalary AS (
    SELECT *
    FROM Employees
    WHERE salary > 45000
)
SELECT *
FROM HighSalary;
```

**Key Points:**
- CTEs are defined using the `WITH` keyword.
- They improve query readability.
- They exist only for the duration of the SQL statement.
- They are useful for breaking complex queries into smaller steps.

---

## 2. CTE with GROUP BY and Aggregate Functions

CTEs can be combined with aggregate functions such as:

- `SUM()`
- `AVG()`
- `COUNT()`
- `MAX()`
- `MIN()`

### Example

Calculate the total salary paid by each department.

```sql
WITH DepartmentSalary AS (
    SELECT
        department,
        SUM(salary) AS total_salary
    FROM Employees
    GROUP BY department
)
SELECT *
FROM DepartmentSalary;
```

**Business Application:**

- Department-wise salary reports.
- Monthly revenue analysis.
- Product-wise sales analysis.
- Customer spending reports.

---

## 3. CTE with HAVING Clause

The `HAVING` clause filters grouped results based on aggregate conditions.

### Example

Find departments where total salary expenditure is greater than 70,000.

```sql
WITH DepartmentSalary AS (
    SELECT
        department,
        SUM(salary) AS total_salary
    FROM Employees
    GROUP BY department
    HAVING SUM(salary) > 70000
)
SELECT *
FROM DepartmentSalary;
```

**Important Difference:**

| WHERE | HAVING |
|---|---|
| Filters individual rows | Filters groups |
| Applied before GROUP BY | Applied after GROUP BY |
| Usually works with row-level conditions | Commonly works with aggregate conditions |

---

## 4. Multiple CTEs in a Single Query

Multiple CTEs can be defined in one SQL statement.

They help organize complex business requirements into multiple steps.

### Example

Find employees earning more than their department's average salary.

```sql
WITH DepartmentAverage AS (
    SELECT
        department,
        AVG(salary) AS avg_salary
    FROM Employees
    GROUP BY department
),
EmployeeDetails AS (
    SELECT
        e.emp_name,
        e.department,
        e.salary,
        d.avg_salary
    FROM Employees e
    JOIN DepartmentAverage d
        ON e.department = d.department
)
SELECT *
FROM EmployeeDetails
WHERE salary > avg_salary;
```

**Key Benefits:**
- Improves readability.
- Reduces repeated query logic.
- Makes debugging easier.
- Separates complex business logic into steps.

---

## 5. CTE with JOIN

CTEs can be combined with JOIN operations to retrieve information from multiple tables.

### Example

Find the total spending of each customer.

```sql
WITH CustomerSpending AS (
    SELECT
        customer_id,
        SUM(amount) AS total_spending
    FROM Orders
    GROUP BY customer_id
)
SELECT
    c.customer_name,
    cs.total_spending
FROM Customers c
JOIN CustomerSpending cs
    ON c.customer_id = cs.customer_id;
```

**Business Applications:**
- Customer purchase analysis.
- Sales performance reports.
- Revenue analysis.
- Customer segmentation.

---

## 6. Recursive CTE

A Recursive CTE is a CTE that refers to itself repeatedly to generate results.

It is useful for hierarchical data and sequential calculations.

### Example

Generate numbers from 1 to 5.

```sql
WITH RECURSIVE NumberSeries AS (
    SELECT 1 AS num

    UNION ALL

    SELECT num + 1
    FROM NumberSeries
    WHERE num < 5
)
SELECT *
FROM NumberSeries;
```

**Output:**

| num |
|---|
| 1 |
| 2 |
| 3 |
| 4 |
| 5 |

**Applications:**
- Employee-manager hierarchies.
- Organizational structures.
- Category hierarchies.
- Generating number sequences.

**Note:** Recursive CTE syntax differs between database systems. For example, SQL Server uses `WITH` without the `RECURSIVE` keyword.

---

## 7. SQL Views

A View is a virtual table created using a SQL query.

It allows users to access frequently required data without repeatedly writing the same query.

### Syntax

```sql
CREATE VIEW HighSalaryEmployees AS
SELECT
    emp_id,
    emp_name,
    department,
    salary
FROM Employees
WHERE salary > 45000;
```

### Retrieve Data from a View

```sql
SELECT *
FROM HighSalaryEmployees;
```

### Filter Data from a View

```sql
SELECT *
FROM HighSalaryEmployees
WHERE department = 'IT';
```

**Benefits of Views:**
- Simplify complex queries.
- Improve query reusability.
- Help manage data access.
- Provide consistent reporting logic.
- Hide unnecessary columns from users.

---

## 8. Difference Between CTE, Subquery, and View

| Feature | Subquery | CTE | View |
|---|---|---|---|
| Syntax | Nested SELECT | WITH | CREATE VIEW |
| Readability | Can become complex | Easy to understand | Reusable |
| Lifetime | Within query | Within statement | Stored definition |
| Reusability | Limited | Within the same statement | Across statements |
| Main Purpose | Nested calculations | Organizing queries | Reusing query logic |

**Important:** CTEs do not automatically improve query performance. Actual performance depends on the database optimizer and query execution plan.

---

## 9. Important SQL Concepts Practiced

| SQL Concept | Purpose |
|---|---|
| WITH | Defines a CTE |
| SUM() | Calculates total values |
| AVG() | Calculates average values |
| GROUP BY | Groups records |
| HAVING | Filters aggregated results |
| JOIN | Combines tables |
| UNION ALL | Combines query results without removing duplicates |
| CREATE VIEW | Creates a database view |
| RECURSIVE | Enables recursive CTEs in supported databases |

## 10. Real-World Applications

These concepts are useful in professional Data Analyst roles.

1. **Sales Analysis:** Calculate total sales by region.
2. **Customer Analysis:** Identify high-value customers.
3. **Employee Analysis:** Compare employee salaries with department averages.
4. **Financial Reporting:** Calculate department-wise expenses.
5. **Business Intelligence:** Prepare reusable datasets for reports and dashboards.
6. **Hierarchical Analysis:** Analyze organizational reporting structures.

## 11. Key Learnings

After completing Day 28, I learned:

- How to create and use CTEs.
- How to combine CTEs with aggregate functions.
- How to filter grouped data using HAVING.
- How to create multiple CTEs in one query.
- How to combine CTEs with JOIN operations.
- How Recursive CTEs work.
- How to create and retrieve data from SQL Views.
- The differences between Subqueries, CTEs, and Views.
