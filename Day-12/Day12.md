# Day 12: Exploratory Data Analysis (EDA) – Patterns, Relationships & Business Insights


# Learning Objectives

By the end of this day, I learned how to:

- Identify patterns in datasets.
- Perform trend analysis and calculate percentage changes.
- Compare sales and performance across categories.
- Analyze relationships between numerical variables.
- Understand correlation and its limitations.
- Perform aggregation and group-wise analysis.
- Identify and investigate potential outliers.
- Select appropriate visualizations for different analytical questions.
- Convert analytical results into actionable business insights.

## 1. Pattern Identification

# Definition

Pattern identification is the process of finding repeated behavior, structures, or relationships within a dataset.

#  Examples

- Identifying the best-selling product.
- Finding regions with consistently low sales.
- Discovering products that generate high revenue.
- Identifying repeated customer purchasing behavior.

### Business Importance

Patterns help businesses understand performance, recognize opportunities, and identify areas requiring improvement.

### Excel Techniques

- PivotTables
- Sorting and filtering
- Conditional formatting
- Bar charts

## 2. Trend Analysis

### Definition

Trend analysis examines how a metric changes over time.

It helps determine whether business performance is improving, declining, or remaining relatively stable.

### Examples

- Monthly sales growth.
- Quarterly profit changes.
- Year-over-year revenue comparison.
- Changes in customer orders over time.

### Percentage Change Formula

Percentage Change = ((New Value - Old Value) / Old Value) × 100

### Example

Previous month's sales = ₹40,000

Current month's sales = ₹45,000

Percentage Change = ((45,000 - 40,000) / 40,000) × 100

**Result: 12.5% increase in sales.**

### Excel Formula

```excel
=(B3-B2)/B2
```

Format the result as a percentage.

**Important:** Percentage change is undefined when the original value is zero. In that situation, use an appropriate alternative comparison.

## 3. Comparative Analysis

### Definition

Comparative analysis compares two or more groups, products, regions, or time periods to identify differences in performance.

### Examples

- Comparing sales across regions.
- Comparing profit across products.
- Comparing current-month and previous-month revenue.
- Comparing actual performance with business targets.

### Absolute Difference Formula

Absolute Difference = New Value - Old Value

### Percentage Change Formula

Percentage Change = ((New Value - Old Value) / Old Value) × 100

### Business Importance

Comparative analysis helps managers identify high-performing categories, investigate underperforming areas, and allocate resources more effectively.

### Excel Tools

- PivotTables
- Bar charts
- Line charts
- Conditional formatting

## 4. Relationship Analysis

### Definition

Relationship analysis investigates whether two variables appear to be associated with each other.

### Examples

- Quantity sold and sales revenue.
- Advertising expenditure and revenue.
- Product discounts and profit.
- Customer satisfaction and repeat purchases.

### Scatter Plot

A scatter plot displays the relationship between two numerical variables.

Possible patterns include:

- **Positive association:** Both variables tend to increase together.
- **Negative association:** One variable tends to decrease as the other increases.
- **No clear linear association:** No obvious straight-line pattern is visible.

### Business Importance

Relationship analysis helps analysts identify variables that may be useful for further investigation.

However, an observed relationship does not automatically prove that one variable causes changes in another.

## 5. Correlation

### Definition

Correlation measures the strength and direction of a linear relationship between two numerical variables.

The Pearson correlation coefficient, represented by `r`, ranges from -1 to +1.

| Correlation Value | Interpretation |
|---|---|
| Close to +1 | Strong positive linear relationship |
| Close to -1 | Strong negative linear relationship |
| Close to 0 | Weak or no linear relationship |

A correlation near zero does not rule out a nonlinear relationship.

### Excel Formula

```excel
=CORREL(B2:B10,C2:C10)
```

This calculates Pearson's correlation coefficient for two corresponding numerical ranges.

### Correlation vs. Causation

**Correlation** means that two variables are associated.

**Causation** means that a change in one variable produces a change in another.

Example: Ice cream sales and swimming activity may both increase during summer because of warmer weather. Their relationship does not prove that one causes the other.

## 6. Aggregation and Group-Wise Analysis

### Definition

Aggregation summarizes multiple records into meaningful metrics.

### Common Aggregation Functions

| Function | Purpose | Excel Formula |
|---|---|---|
| SUM | Calculates the total | `=SUM(D2:D100)` |
| AVERAGE | Calculates the arithmetic mean | `=AVERAGE(D2:D100)` |
| COUNT | Counts numerical cells | `=COUNT(D2:D100)` |
| COUNTA | Counts non-empty cells | `=COUNTA(A2:A100)` |
| MIN | Finds the minimum value | `=MIN(D2:D100)` |
| MAX | Finds the maximum value | `=MAX(D2:D100)` |
| MEDIAN | Finds the middle value | `=MEDIAN(D2:D100)` |

### SQL Example

```sql
SELECT
    Region,
    SUM(Sales) AS Total_Sales,
    SUM(Profit) AS Total_Profit
FROM Sales
GROUP BY Region;
```

### Explanation

- `SELECT` specifies the output columns.
- `SUM(Sales)` calculates total sales.
- `SUM(Profit)` calculates total profit.
- `GROUP BY Region` groups records by region.

This query returns summarized sales and profit for each region.

## 7. Outlier Analysis

### Definition

An outlier is an observation that differs substantially from the rest of the data.

### Example

Consider the following order values:

₹1,000, ₹1,200, ₹1,100, ₹1,300, ₹1,250, ₹50,000

The ₹50,000 order is much larger than the other observations and may be an outlier.

### Why Outliers Matter

Outliers can affect:

- Mean calculations.
- Correlation coefficients.
- Statistical models.
- Data visualizations.
- Business conclusions.

### Interquartile Range (IQR) Method

IQR = Q3 - Q1

Where:

- Q1 represents the first quartile.
- Q3 represents the third quartile.

Lower Fence = Q1 - 1.5 × IQR

Upper Fence = Q3 + 1.5 × IQR

Values outside these fences are commonly flagged as potential outliers.

### How to Handle Outliers

1. Verify the original source data.
2. Check for data-entry errors.
3. Investigate possible business explanations.
4. Correct or exclude values only when justified.
5. Document the decision.

**Important:** An outlier is not automatically an error. It may represent a genuine business event.

## 8. Business Insight Generation

### Definition

Business insight generation involves interpreting analytical results to understand what is happening and determine what action should be investigated or taken next.

### Four-Step Framework

1. **Question:** Identify the business problem.
2. **Analysis:** Calculate relevant metrics and examine the data.
3. **Insight:** Explain what the results indicate.
4. **Action:** Recommend an appropriate next step.

### Example

**Observation:** Laptop sales are ₹1,55,000, mobile sales are ₹75,000, and headphone sales are ₹25,000 in the sample dataset.

**Insight:** Laptops generate the highest total sales among the three products.

**Recommended next step:** Investigate laptop profit margins, inventory availability, and customer demand before deciding whether to increase inventory.

A good business insight includes evidence and avoids unsupported conclusions.

## 9. Data Visualization for EDA

Data visualization presents analytical results graphically, making patterns and comparisons easier to understand.

| Visualization | Purpose |
|---|---|
| Bar Chart | Compare categories |
| Line Chart | Analyze changes over time |
| Scatter Plot | Explore relationships between numerical variables |
| Box Plot | Examine distributions and potential outliers |
| Histogram | Understand the distribution of a numerical variable |

### Visualization Best Practices

- Select a chart that matches the analytical question.
- Include clear titles, labels, and units.
- Avoid unnecessary colors and decorative elements.
- Ensure the axis scale does not misrepresent differences.
- Explain the main finding instead of presenting a chart without context.

## 10. Complete EDA Workflow

A systematic EDA workflow includes:

1. Understand the dataset and its business context.
2. Inspect data types and column meanings.
3. Check missing values, duplicates, and invalid records.
4. Calculate descriptive statistics.
5. Explore patterns and trends.
6. Compare categories and time periods.
7. Investigate relationships and potential outliers.
8. Validate findings and consider alternative explanations.
9. Create meaningful visualizations.
10. Communicate insights and recommended next steps.

EDA is an iterative process. Unexpected findings may require additional data-quality checks or further analysis.

# Practical Dataset

The following sample dataset represents e-commerce transactions.

| Order ID | Region | Product | Sales (₹) | Profit (₹) | Quantity |
|---|---|---|---:|---:|---:|
| 101 | South | Laptop | 50,000 | 8,000 | 2 |
| 102 | North | Mobile | 30,000 | 4,500 | 3 |
| 103 | South | Mobile | 20,000 | 2,000 | 2 |
| 104 | East | Laptop | 60,000 | 6,000 | 2 |
| 105 | North | Headphones | 10,000 | 2,500 | 5 |
| 106 | East | Mobile | 25,000 | 3,000 | 2 |
| 107 | South | Headphones | 15,000 | -1,000 | 3 |
| 108 | North | Laptop | 45,000 | 7,000 | 1 |

### Practice Tasks

1. Calculate total sales by product.
2. Calculate total profit by region.
3. Identify the highest-selling product.
4. Calculate the percentage change between two monthly sales values.
5. Create a monthly sales trend chart.
6. Investigate the negative-profit order.
7. Identify potential relationships between quantity and sales.
8. Write three evidence-based business insights.

# Sample Findings

- Total sales across all eight orders are ₹2,55,000.
- Laptops generate the highest product-level sales at ₹1,55,000.
- The South, North, and East regions each generate ₹85,000 in sales.
- Order 107 has negative profit and should be investigated rather than automatically removed.

# Key Learnings

- EDA helps analysts understand data before drawing conclusions.
- Patterns reveal repeated behavior in datasets.
- Trend analysis examines changes over time.
- Comparative analysis identifies differences between groups.
- Correlation measures linear association but does not prove causation.
- Aggregation simplifies large datasets into useful summaries.
- Outliers should be investigated before being removed.
- Visualization makes analytical findings easier to communicate.
- Business insights connect data evidence to decisions.

# Tools and Technologies

- Microsoft Excel
- PivotTables
- Excel formulas
- Data visualization
- SQL aggregation
- Exploratory Data Analysis concepts
- Business intelligence fundamentals

