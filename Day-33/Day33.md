# Day 33 – Advanced Power Query Concepts

## Introduction
Today, I learned Advanced Power Query operations in Power BI. Power Query helps Data Analysts combine, transform, summarize, and prepare raw data before creating reports and dashboards.

## Topics Covered

### 1. Merge Queries
Merge Queries combines two tables using a common column. It works similarly to SQL JOIN operations.

**Example:** Combining Employee and Salary tables using EmployeeID.

**Uses:**
- Combining data from multiple sources.
- Adding related information to existing tables.
- Connecting employee details with salary information.

### 2. Append Queries
Append Queries combines two or more tables by adding their rows into a single table.

**Example:** Combining January Sales and February Sales into one sales table.

**Uses:**
- Combining monthly sales reports.
- Merging yearly datasets.
- Combining similar tables from different sources.

**Difference:**
- Merge combines columns.
- Append combines rows.

### 3. Group By
Group By summarizes data based on common column values.

**Example:** Calculating total salary department-wise.

**Common Operations:**
- Sum – Calculates total values.
- Average – Calculates average values.
- Count Rows – Counts records.
- Minimum – Finds the smallest value.
- Maximum – Finds the largest value.

### 4. Conditional Column
A Conditional Column creates a new column based on specified conditions.

**Example:**

If Marks >= 40, Result = Pass; otherwise, Result = Fail.

**Uses:**
- Categorizing sales performance.
- Identifying pass and fail results.
- Creating employee performance categories.

### 5. Custom Column
A Custom Column allows us to create new columns using formulas written in Power Query M language.

**Example:**

```powerquery
[Quantity] * [Price]
```

This formula calculates the total amount using quantity and price.

**Uses:**
- Calculating total revenue.
- Calculating discounts.
- Creating profit calculations.
- Performing custom data transformations.

## Difference Between Merge and Append

| Merge Queries | Append Queries |
|---|---|
| Combines columns | Combines rows |
| Uses common columns | Stacks tables vertically |
| Similar to SQL JOIN | Similar to UNION ALL |

## Practical Applications
1. Combining employee and salary datasets.
2. Combining monthly sales reports.
3. Calculating department-wise totals.
4. Creating conditional categories.
5. Calculating revenue using custom formulas.

## Key Takeaways
- Learned how to combine multiple tables using Merge Queries.
- Understood how Append Queries combines rows.
- Learned how to summarize information using Group By.
- Understood how to create Conditional Columns.
- Practiced creating Custom Columns using M language.
- Understood how Power Query prepares data for Power BI reports.

