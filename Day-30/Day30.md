# Day 30 - Advanced SQL Analytical Problem-Solving

## 1. Running Total

A Running Total is the cumulative sum of values calculated over a sequence of rows.

**Purpose:**
- Track cumulative sales over time.
- Monitor total revenue growth.
- Analyze business performance.

**SQL Query:**

```sql
SELECT
    order_date,
    amount,
    SUM(amount) OVER (
        ORDER BY order_date, order_id
        ROWS BETWEEN UNBOUNDED PRECEDING
        AND CURRENT ROW
    ) AS running_total
FROM orders;
```

**Key Concepts:**
- `SUM()` calculates the total amount.
- `OVER()` performs a window calculation.
- `ORDER BY` defines the calculation sequence.
- `UNBOUNDED PRECEDING` starts from the first row.
- `CURRENT ROW` includes the current row.

## 2. Month-over-Month (MoM) Analysis

Month-over-Month analysis compares the sales performance of the current month with the previous month.

**Purpose:**
- Identify monthly sales growth.
- Understand business performance.
- Identify increases and decreases in revenue.

**Formula:**

MoM Growth Percentage =

(Current Month Sales - Previous Month Sales) / Previous Month Sales × 100

**SQL Concepts Used:**
- `GROUP BY`
- `SUM()`
- `LAG()`
- `ROUND()`
- CTE

**Example:**

```sql
LAG(total_sales) OVER (
    ORDER BY sales_month
) AS previous_month_sales
```

The `LAG()` function retrieves the previous month's sales for comparison.

## 3. Top N Products in Each Category

This technique identifies the highest-performing products within each category.

**Purpose:**
- Identify best-selling products.
- Compare product performance.
- Support business decisions.

**SQL Query:**

```sql
WITH product_sales AS (
    SELECT
        category,
        product,
        SUM(amount) AS total_revenue
    FROM orders
    GROUP BY category, product
),
ranked_products AS (
    SELECT
        category,
        product,
        total_revenue,
        DENSE_RANK() OVER (
            PARTITION BY category
            ORDER BY total_revenue DESC
        ) AS product_rank
    FROM product_sales
)
SELECT *
FROM ranked_products
WHERE product_rank <= 3;
```

**Key Concepts:**
- `PARTITION BY` creates separate category groups.
- `DENSE_RANK()` assigns rankings without gaps.
- `ORDER BY DESC` ranks the highest revenue first.

## 4. Returning Customer Analysis

Returning customers are customers who purchase products more than once.

**Purpose:**
- Identify loyal customers.
- Understand customer purchasing behavior.
- Measure customer retention.

**SQL Query:**

```sql
SELECT
    customer,
    COUNT(order_id) AS total_orders,
    SUM(amount) AS total_spent
FROM orders
GROUP BY customer
HAVING COUNT(order_id) > 1;
```

**Key Concepts:**
- `COUNT()` counts customer orders.
- `SUM()` calculates total spending.
- `GROUP BY` groups records by customer.
- `HAVING` filters aggregated results.

## 5. Products Performing Above Average

This analysis identifies products generating revenue greater than the average product revenue.

**Purpose:**
- Identify high-performing products.
- Compare product revenue.
- Support inventory and marketing decisions.

**SQL Query:**

```sql
WITH product_sales AS (
    SELECT
        product,
        SUM(amount) AS total_revenue
    FROM orders
    GROUP BY product
)
SELECT *
FROM product_sales
WHERE total_revenue > (
    SELECT AVG(total_revenue)
    FROM product_sales
);
```

**Key Concepts:**
- CTE prepares product-level revenue.
- Subquery calculates average revenue.
- `WHERE` filters products above the average.

## 6. Moving Average

A Moving Average calculates the average value over a fixed number of preceding rows and the current row.

**Purpose:**
- Identify sales trends.
- Reduce short-term fluctuations.
- Understand business performance over time.

**SQL Query:**

```sql
AVG(total_sales) OVER (
    ORDER BY sales_month
    ROWS BETWEEN 2 PRECEDING
    AND CURRENT ROW
) AS moving_average
```

This example calculates a three-row moving average using the current row and two previous rows.

## 7. Highest Order for Each Customer

This technique identifies the highest-value order placed by each customer.

**Purpose:**
- Analyze customer purchasing behavior.
- Identify high-value transactions.
- Understand customer spending patterns.

**SQL Query:**

```sql
WITH customer_orders AS (
    SELECT
        customer,
        order_id,
        product,
        amount,
        ROW_NUMBER() OVER (
            PARTITION BY customer
            ORDER BY amount DESC
        ) AS rn
    FROM orders
)
SELECT *
FROM customer_orders
WHERE rn = 1;
```

**Key Concepts:**
- `ROW_NUMBER()` assigns unique row numbers.
- `PARTITION BY` separates customers.
- `ORDER BY DESC` places the highest order first.

## 8. Sales Contribution Percentage

Sales Contribution Percentage measures how much each product contributes to the company's total revenue.

**Formula:**

Contribution Percentage = (Product Revenue / Total Revenue) × 100

**SQL Query:**

```sql
WITH product_sales AS (
    SELECT
        product,
        SUM(amount) AS total_revenue
    FROM orders
    GROUP BY product
)
SELECT
    product,
    total_revenue,
    ROUND(
        total_revenue * 100.0 /
        SUM(total_revenue) OVER (),
        2
    ) AS contribution_percentage
FROM product_sales;
```

**Purpose:**
- Understand product revenue contribution.
- Identify important revenue-generating products.
- Support business planning.

## 9. Important SQL Concepts Practiced

| SQL Concept | Purpose |
|---|---|
| SUM() | Calculates total values |
| COUNT() | Counts records |
| GROUP BY | Groups similar records |
| HAVING | Filters aggregated data |
| CTE | Organizes complex queries |
| Subquery | Performs nested calculations |
| LAG() | Retrieves previous row values |
| ROW_NUMBER() | Assigns unique row numbers |
| DENSE_RANK() | Ranks records without gaps |
| PARTITION BY | Divides data into groups |
| OVER() | Performs window calculations |
| AVG() | Calculates averages |
| NULLIF() | Prevents division-by-zero errors |

## 10. Real-World Applications

These SQL techniques are useful in:

- E-commerce sales analysis.
- Customer purchasing analysis.
- Monthly revenue reporting.
- Product performance analysis.
- Business performance dashboards.
- Customer retention analysis.
- Sales forecasting and trend analysis.

# Learned Topics

After completing Day 30, I understood how to:

- Calculate running totals using window functions.
- Perform Month-over-Month sales analysis.
- Calculate percentage growth.
- Identify top-performing products in each category.
- Find returning customers.
- Compare product revenue against average revenue.
- Calculate moving averages.
- Identify the highest-value customer orders.
- Calculate product contribution percentages.
- Combine CTEs, subqueries, aggregate functions, and window functions.
