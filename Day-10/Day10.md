# Day 10 - Exploratory Data Analysis (EDA)


# Learning Objectives

By the end of this challenge, I learned about:

- Understanding dataset structure and data types.
- Calculating descriptive statistics.
- Understanding data distributions.
- Identifying and investigating potential outliers.
- Exploring relationships between numerical variables.
- Grouping and analyzing data by categories.
- Performing time-based analysis.
- Selecting appropriate charts for different analytical questions.
- Exploring data using Excel and Power BI.
- Converting analytical findings into business insights.

# 1. What Is Exploratory Data Analysis?

Exploratory Data Analysis (EDA) is the process of examining and summarizing data to understand its characteristics, patterns, relationships, and potential problems.

EDA helps Data Analysts answer questions such as:

- Which product generates the highest revenue?
- Which region performs best?
- What is the average order value?
- Are there any unusual transactions?
- How does revenue change over time?
- Are two numerical variables related?

### Why Is EDA Important?

EDA helps analysts understand their data before drawing conclusions. It reduces the risk of misleading interpretations and helps identify useful business questions.

## 2. Steps in Exploratory Data Analysis

### Step 1: Understand the Dataset

Inspect the dataset to understand:

- Number of rows and columns.
- Column names and meanings.
- Data types.
- Unique values and categories.
- What each row represents.

### Step 2: Check Data Quality

Look for:

- Missing values.
- Duplicate records.
- Incorrect data types.
- Inconsistent categories.
- Invalid or suspicious values.

### Step 3: Calculate Summary Statistics

Calculate totals, averages, medians, minimums, maximums, and measures of variation.

### Step 4: Explore Patterns and Relationships

Compare categories, examine trends, and investigate relationships between variables.

### Step 5: Generate Insights

Summarize findings, explain their business meaning, and identify questions that require further investigation.

## 3. Descriptive Statistics

Descriptive statistics summarize the important characteristics of a dataset.

### A. Sum

The sum calculates the total of all numerical values.

**Formula:**

Total = Sum of all observations

**Excel formula:**

```excel
=SUM(F2:F9)
```

**Business use:** Calculate total sales revenue.

### B. Mean (Average)

The mean is calculated by dividing the sum of all observations by the number of observations.

**Formula:**

Mean = Sum of values / Number of observations

**Excel formula:**

```excel
=AVERAGE(F2:F9)
```

**Business use:** Calculate average order revenue.

### C. Median

The median is the middle value after sorting the observations.

**Excel formula:**

```excel
=MEDIAN(F2:F9)
```

The median is useful when unusually large or small values influence the mean.

### D. Minimum and Maximum

Minimum identifies the smallest value, while maximum identifies the largest value.

**Excel formulas:**

```excel
=MIN(F2:F9)
=MAX(F2:F9)
```

### E. Range

Range measures the difference between the maximum and minimum values.

**Formula:**

Range = Maximum - Minimum

### F. Standard Deviation

Standard deviation measures how spread out the values are around their mean.

**Excel formulas:**

```excel
=STDEV.S(F2:F9)
=STDEV.P(F2:F9)
```

Use `STDEV.S` for sample data and `STDEV.P` for the full population being analyzed.

## 4. Understanding Data Distributions

A data distribution describes how values are spread across a dataset.

Common patterns include:

- **Symmetric distribution:** Values are distributed fairly evenly around the center.
- **Right-skewed distribution:** A small number of high values create a longer right tail.
- **Left-skewed distribution:** A small number of low values create a longer left tail.

A histogram helps visualize the frequency of values within numerical intervals.

**Business example:** A histogram of order revenue can show whether most orders have low values and a few orders have exceptionally high values.

## 5. Outlier Detection

An outlier is an observation that is unusually far from other observations.

Outliers may result from genuine business activity, data-entry errors, unusual events, or other factors. They should be investigated rather than automatically removed.

### Interquartile Range (IQR) Method

IQR measures the spread of the middle 50% of the data.

**Formula:**

IQR = Q3 - Q1

Where:
- Q1 is the first quartile (25th percentile).
- Q3 is the third quartile (75th percentile).

**Lower fence:**

Lower Fence = Q1 - 1.5 × IQR

**Upper fence:**

Upper Fence = Q3 + 1.5 × IQR

Values outside these fences are potential outliers that require further investigation.

**Excel formulas:**

```excel
=QUARTILE.INC(F2:F101,1)
=QUARTILE.INC(F2:F101,3)
```

## 6. Correlation Analysis

Correlation measures the strength and direction of a linear relationship between two numerical variables.

The correlation coefficient ranges from -1 to +1.

- **Close to +1:** Strong positive linear relationship.
- **Close to 0:** Little or no linear relationship.
- **Close to -1:** Strong negative linear relationship.

**Excel formula:**

```excel
=CORREL(B2:B101,C2:C101)
```

**Business example:** Analyze the relationship between advertising spending and sales revenue.

**Important:** Correlation does not prove causation. Other factors may influence the relationship.

A scatter plot helps visualize the relationship between two numerical variables.

## 7. Grouping and Segmentation

Grouping summarizes data by categories such as product, region, department, or month.

For example, total revenue by product helps identify which products contribute the most revenue.

**Excel formula:**

```excel
=SUMIF(B2:B9,"Laptop",F2:F9)
```

Here:
- Column B contains product names.
- Column F contains revenue.
- The formula calculates revenue for Laptop orders.

PivotTables can also summarize revenue by product, region, or other categories.

## 8. Time-Based Analysis

Time-based analysis examines how business metrics change over time.

Common questions include:

- Is revenue increasing or decreasing?
- Which month has the highest revenue?
- Are seasonal patterns present?
- How does this month compare with the previous month?

### Month-over-Month Growth

**Formula:**

Growth % = ((Current Period - Previous Period) / Previous Period) × 100

**Excel formula:**

```excel
=(B3-B2)/B2
```

Format the result as a percentage.

A line chart is useful for visualizing changes over time.

## 9. Data Visualization Techniques

Choosing an appropriate chart makes analytical findings easier to understand.

| Visualization | Purpose | Example |
|---|---|---|
| Bar Chart | Compare categories | Revenue by product |
| Line Chart | Show changes over time | Monthly revenue |
| Histogram | Understand distributions | Distribution of order values |
| Scatter Plot | Explore relationships | Advertising spending vs. revenue |
| Box Plot | Examine spread and potential outliers | Revenue distribution by region |

Charts should be selected according to the question being investigated.

## 10. Exploratory Data Analysis Using Excel

Excel provides several tools for performing EDA:

- `SUM()` for totals.
- `AVERAGE()` for mean values.
- `MEDIAN()` for median values.
- `MIN()` and `MAX()` for extreme values.
- `STDEV.S()` for sample standard deviation.
- `CORREL()` for correlation.
- `SUMIF()` for conditional aggregation.
- PivotTables for summarizing data.
- Charts for visual exploration.
- Conditional Formatting for highlighting unusual values.

## 11. Exploratory Data Analysis Using Power BI

Power BI supports data exploration and reporting through:

1. **Get Data:** Import data from Excel, CSV files, and other sources.
2. **Power Query:** Inspect, clean, and transform data.
3. **Data Model:** Organize tables and relationships.
4. **DAX Measures:** Calculate business metrics.
5. **Visualizations:** Compare products, regions, and time periods.
6. **Filters and Slicers:** Explore different subsets of data.

### Example DAX Measure

```dax
Total Revenue =
SUM(Sales[Revenue])
```

This measure calculates total revenue and responds to the report's filter context.

## 12. Practical Exercise: Sales Data Analysis

For this challenge, I practiced analyzing a sample sales dataset containing:

- Order ID
- Product
- Region
- Quantity
- Unit Price
- Revenue

### Revenue Calculation

Revenue = Quantity × Unit Price

**Example:**

Quantity = 2

Unit Price = ₹40,000

Revenue = 2 × ₹40,000 = ₹80,000

# Tasks

1. Calculate revenue for each order.
2. Calculate total revenue and average revenue.
3. Find the median, minimum, and maximum revenue.
4. Calculate revenue by product.
5. Compare revenue across regions.
6. Create bar charts for product and regional comparisons.
7. Identify unusual values that require investigation.
8. Write at least three observations from the dataset.

# 13. Key Learnings

Through Day 10, I learned that:

- EDA is essential before drawing conclusions from data.
- Summary statistics help describe datasets.
- Mean and median provide different perspectives on central tendency.
- Standard deviation measures variation.
- Distributions reveal how values are spread.
- Potential outliers require investigation.
- Correlation helps explore relationships but does not prove causation.
- Grouping makes category-level comparisons possible.
- Time-based analysis helps identify changes and potential trends.
- Appropriate visualizations make patterns easier to understand.
- Excel and Power BI provide practical tools for data exploration.

