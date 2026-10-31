# Day 23 – Advanced SQL JOINs & Multiple Table JOINs


## 1. Multiple Table JOINs

A Multiple Table JOIN combines data from three or more tables using common columns or relationships.

### Example:

```sql
SELECT
    c.customer_name,
    o.order_id,
    p.product_name,
    oi.quantity,
    p.price
FROM Customers c

INNER JOIN Orders o
    ON c.customer_id = o.customer_id

INNER JOIN Order_Items oi
    ON o.order_id = oi.order_id

INNER JOIN Products p
    ON oi.product_id = p.product_id;
```

### Key Points

- Multiple JOIN statements can be used in a single query.
- Each JOIN connects another related table.
- Table aliases make complex queries easier to read.
- Multiple JOINs are commonly used in business reporting.

---

## 2. Understanding Table Relationships

Relational databases use different types of relationships to connect tables.

### A. One-to-One (1:1)

One record in a table is associated with only one record in another table.

Example: Employee and Employee Profile.

### B. One-to-Many (1:M)

One record in a table can be associated with multiple records in another table.

Example: One customer can place multiple orders.

### C. Many-to-Many (M:M)

Multiple records in one table can be associated with multiple records in another table.

Example: Orders and Products.

A junction table or bridge table is used to manage this relationship.

---

## 3. JOIN with GROUP BY

GROUP BY is used to combine rows with the same values into groups.

When combined with JOINs, it helps generate summarized business reports.

### Example: Calculate Total Spending by Customer

```sql
SELECT
    c.customer_name,
    SUM(oi.quantity * p.price) AS total_spending

FROM Customers c

JOIN Orders o
    ON c.customer_id = o.customer_id

JOIN Order_Items oi
    ON o.order_id = oi.order_id

JOIN Products p
    ON oi.product_id = p.product_id

GROUP BY c.customer_id, c.customer_name;
```

### Revenue Formula

**Revenue = Quantity × Price**

GROUP BY helps calculate customer-level, product-level, and category-level business metrics.

---

## 4. JOIN with HAVING

HAVING is used to filter grouped results after GROUP BY.

### Example:

Find customers whose total spending is greater than ₹50,000.

```sql
SELECT
    c.customer_name,
    SUM(oi.quantity * p.price) AS total_spending

FROM Customers c

JOIN Orders o
    ON c.customer_id = o.customer_id

JOIN Order_Items oi
    ON o.order_id = oi.order_id

JOIN Products p
    ON oi.product_id = p.product_id

GROUP BY c.customer_id, c.customer_name

HAVING SUM(oi.quantity * p.price) > 50000;
```

### WHERE vs HAVING

| WHERE | HAVING |
|---|---|
| Filters individual rows | Filters grouped results |
| Used before GROUP BY | Used after GROUP BY |
| Filters row-level data | Filters aggregate results |

---

## 5. LEFT JOIN and Anti-Join Pattern

LEFT JOIN returns all records from the left table, including records without matching rows in the right table.

### Example: Find Customers Without Orders

```sql
SELECT
    c.customer_name
FROM Customers c

LEFT JOIN Orders o
    ON c.customer_id = o.customer_id

WHERE o.order_id IS NULL;
```

### Real-World Applications

- Finding customers who never purchased products.
- Finding products that were never sold.
- Finding employees without assigned projects.
- Identifying missing relationships between tables.

---

## 6. Subqueries and Common Table Expressions (CTEs)

A subquery is a query written inside another SQL query.

A CTE is a temporary named result set created using the WITH clause.

### Example: Customer Spending Using CTE

```sql
WITH CustomerSpending AS (
    SELECT
        c.customer_id,
        c.customer_name,
        SUM(oi.quantity * p.price) AS total_spending

    FROM Customers c

    JOIN Orders o
        ON c.customer_id = o.customer_id

    JOIN Order_Items oi
        ON o.order_id = oi.order_id

    JOIN Products p
        ON oi.product_id = p.product_id

    GROUP BY c.customer_id, c.customer_name
)

SELECT *
FROM CustomerSpending;
```

### Finding Customers Spending Above Average

```sql
WITH CustomerSpending AS (
    SELECT
        c.customer_id,
        c.customer_name,
        SUM(oi.quantity * p.price) AS total_spending

    FROM Customers c

    JOIN Orders o
        ON c.customer_id = o.customer_id

    JOIN Order_Items oi
        ON o.order_id = oi.order_id

    JOIN Products p
        ON oi.product_id = p.product_id

    GROUP BY c.customer_id, c.customer_name
)

SELECT *
FROM CustomerSpending
WHERE total_spending > (
    SELECT AVG(total_spending)
    FROM CustomerSpending
);
```

---

## 7. Duplicate Records in Multiple JOINs

One important concept I learned today is that multiple JOINs can increase the number of rows in a result.

For example:

- One customer has two orders.
- Each order contains three products.
- Joining the tables produces six order-item rows for that customer.

This is expected behavior when joining one-to-many relationships.

### What is Join Fan-Out?

Join fan-out occurs when a JOIN expands rows because one record matches multiple records in another table.

### How to Avoid Incorrect Calculations

- Understand the grain of each table.
- Use COUNT(DISTINCT column) when counting unique entities.
- Aggregate data at the correct level before joining.
- Avoid blindly using SUM() on repeated values.

### Example:

```sql
SELECT
    c.customer_name,
    COUNT(DISTINCT o.order_id) AS total_orders

FROM Customers c

JOIN Orders o
    ON c.customer_id = o.customer_id

GROUP BY c.customer_id, c.customer_name;
```

---

## 8. Fact Tables and Dimension Tables

### Fact Table

A Fact Table stores measurable business events and numerical values.

Examples:

- Sales amount
- Quantity sold
- Profit
- Transaction amount
- Order count

### Dimension Table

A Dimension Table stores descriptive information used to analyze business events.

Examples:

- Customer details
- Product details
- Date details
- Location details

### Example: Sales by Product Category

```sql
SELECT
    p.category,
    SUM(f.sales) AS total_sales

FROM Sales_Fact f

JOIN Products_Dim p
    ON f.product_id = p.product_id

GROUP BY p.category;
```

### What is a Star Schema?

A Star Schema is a data warehouse modeling structure in which a central fact table connects to multiple dimension tables.

This concept is important for Power BI data modeling and analytical reporting.

---

## 9. SQL Logical Execution Order

The simplified logical execution order of SQL is:

1. FROM
2. JOIN / ON
3. WHERE
4. GROUP BY
5. HAVING
6. SELECT
7. DISTINCT
8. ORDER BY
9. LIMIT / FETCH

Understanding SQL execution order helps write better queries and understand why certain SQL clauses are used in specific places.

---

## 10. Real-World Business Applications

Today, I practiced SQL queries for the following business requirements:

### 1. Calculate Total Revenue

```sql
SELECT
    SUM(oi.quantity * p.price) AS total_revenue
FROM Orders o

JOIN Order_Items oi
    ON o.order_id = oi.order_id

JOIN Products p
    ON oi.product_id = p.product_id;
```

### 2. Find the Top-Selling Product

```sql
SELECT
    p.product_name,
    SUM(oi.quantity) AS total_quantity

FROM Order_Items oi

JOIN Products p
    ON oi.product_id = p.product_id

GROUP BY p.product_id, p.product_name

ORDER BY total_quantity DESC

LIMIT 1;
```

### 3. Find Revenue by City

```sql
SELECT
    c.city,
    SUM(oi.quantity * p.price) AS total_revenue

FROM Customers c

JOIN Orders o
    ON c.customer_id = o.customer_id

JOIN Order_Items oi
    ON o.order_id = oi.order_id

JOIN Products p
    ON oi.product_id = p.product_id

GROUP BY c.city

ORDER BY total_revenue DESC;
```

### 4. Find Customers with More Than Two Orders

```sql
SELECT
    c.customer_name,
    COUNT(DISTINCT o.order_id) AS total_orders

FROM Customers c

JOIN Orders o
    ON c.customer_id = o.customer_id

GROUP BY c.customer_id, c.customer_name

HAVING COUNT(DISTINCT o.order_id) > 2;
```

---

## 11. Key Concepts Learned

| Concept | Description |
|---|---|
| Multiple JOINs | Combining three or more tables |
| Table Relationships | 1:1, 1:M, and M:M |
| GROUP BY | Grouping records |
| HAVING | Filtering grouped results |
| LEFT JOIN | Preserving all left-table records |
| Anti-Join | Finding unmatched records |
| Subquery | Query inside another query |
| CTE | Temporary named query result |
| Join Fan-Out | Row expansion after JOINs |
| Fact Table | Stores measurable business events |
| Dimension Table | Stores descriptive attributes |
| Star Schema | Fact and dimension table structure |


## 12. Day 23 Practice Questions

I practiced and explored the following SQL problems:

1. Display customer names with their order IDs.
2. Display customers with their purchased product names.
3. Calculate total spending for each customer.
4. Find total revenue by product category.
5. Find customers who have never placed orders.
6. Find the product with the highest quantity sold.
7. Display cities ranked by total revenue.
8. Find customers who have placed more than two orders.
9. Calculate average spending per customer.
10. Find the top three customers based on total spending.

---

# Important Takeaways

- Real-world business databases contain multiple related tables.
- Multiple JOINs help combine information from different tables.
- GROUP BY and aggregate functions generate business summaries.
- HAVING filters grouped results.
- LEFT JOIN helps identify missing relationships.
- CTEs make complex queries more readable.
- Understanding table grain helps prevent incorrect calculations.
- Fact Tables and Dimension Tables are important for data warehousing.
- SQL JOINs are essential for creating reliable analytical reports.



