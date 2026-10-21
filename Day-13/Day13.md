# Day 13: Exploratory Data Analysis (EDA) – Statistical Analysis and Business Insights

# Overview

Day 13 of my **60-Day Data Analyst Challenge** focuses on Exploratory Data Analysis (EDA), a fundamental process used to understand datasets, identify patterns, detect unusual observations, and generate meaningful business insights.

The objective of this challenge is to learn how to analyze data systematically using statistical methods, data grouping, correlation analysis, and visualization techniques.

# Learning Objectives

- Understand the importance of Exploratory Data Analysis.
- Calculate and interpret summary statistics.
- Understand numerical distributions and their shapes.
- Identify and investigate potential outliers.
- Understand correlation between numerical variables.
- Perform grouped analysis using categories.
- Analyze trends and changes over time.
- Select appropriate visualizations for analytical questions.
- Convert analytical results into actionable business insights.

# 1. What Is Exploratory Data Analysis (EDA)?

Exploratory Data Analysis is the process of examining and analyzing a dataset to understand its structure, quality, patterns, relationships, and unusual observations before drawing conclusions.

# Why Is EDA Important?

- Helps identify missing values and data quality issues.
- Provides an overview of the dataset.
- Reveals patterns and relationships between variables.
- Helps detect unusual observations.
- Supports better business decisions.
- Helps determine which further analyses are required.

# EDA Workflow

1. Understand the business problem.
2. Inspect the dataset and its structure.
3. Validate data quality.
4. Calculate summary statistics.
5. Explore distributions and relationships.
6. Visualize important patterns.
7. Communicate findings and business insights.

# 2. Summary Statistics

Summary statistics describe the main characteristics of numerical data.

| Statistical Measure | Description |
|---|---|
| Count | Number of observations |
| Sum | Total of all numerical values |
| Mean | Arithmetic average |
| Median | Middle value of sorted observations |
| Minimum | Smallest observed value |
| Maximum | Largest observed value |
| Range | Difference between maximum and minimum |
| Standard Deviation | Measures the spread of observations around the mean |

# Important Formulas

**Mean:**

Mean = Sum of all observations / Number of observations

**Range:**

Range = Maximum Value - Minimum Value

**Population Standard Deviation:**

σ = √[Σ(xᵢ - μ)² / N]

**Sample Standard Deviation:**

s = √[Σ(xᵢ - x̄)² / (n - 1)]

### Example

Consider the following order revenue values:

`2500, 3000, 5000, 40000, 40000, 80000`

- Total Revenue = ₹170,500
- Mean Revenue = ₹28,416.67
- Median Revenue = ₹22,500
- Minimum Revenue = ₹2,500
- Maximum Revenue = ₹80,000
- Range = ₹77,500

**Business Insight:** The mean is higher than the median because the dataset contains some high-value orders.

## 3. Distribution Analysis

A distribution describes how values are spread across a dataset and how frequently different values occur.

### Types of Distributions

**Normal Distribution**
- Symmetrical, bell-shaped distribution.
- Mean, median, and mode coincide in an ideal normal distribution.
- Approximately 68%, 95%, and 99.7% of observations lie within one, two, and three standard deviations of the mean, respectively.

**Right-Skewed Distribution**
- Has a longer tail toward higher values.
- Often occurs in income and transaction-value data.
- The mean is often greater than the median.

**Left-Skewed Distribution**
- Has a longer tail toward lower values.
- The mean is often less than the median.

**Uniform Distribution**
- Values or intervals have approximately equal probabilities or frequencies, depending on the distribution.

### Why Distribution Analysis Matters

- Helps understand data variability.
- Shows whether the mean represents a typical observation.
- Helps identify potential outliers.
- Supports the selection of suitable statistical methods and visualizations.

## 4. Outlier Detection

An outlier is an observation that differs substantially from the general pattern of the dataset.

Outliers may occur because of:
- Data-entry mistakes.
- Measurement errors.
- Unusual customer behavior.
- Large transactions.
- Genuine business events.

### Method 1: Interquartile Range (IQR)

IQR measures the spread of the middle 50% of observations.

**Formula:**

IQR = Q3 - Q1

Lower Bound = Q1 - 1.5 × IQR

Upper Bound = Q3 + 1.5 × IQR

Observations outside these bounds are flagged as potential outliers.

### Method 2: Z-Score

A Z-score measures how many standard deviations an observation lies from the mean.

**Formula:**

Z = (x - μ) / σ

An absolute Z-score greater than 3 is a commonly used screening rule for potential outliers, particularly for approximately normal data.

### Best Practices

1. Identify unusual observations.
2. Validate the original data.
3. Investigate possible causes.
4. Determine whether the observation is valid.
5. Decide whether to retain, correct, exclude, or analyze it separately.
6. Document the decision.

**Important:** Outliers should not be deleted automatically. A high-value transaction may represent a genuine business event.

## 5. Correlation Analysis

Correlation measures the strength and direction of association between two numerical variables.

### Types of Correlation

**Positive Correlation:** Both variables tend to increase together.

**Negative Correlation:** One variable tends to increase as the other decreases.

**Zero or Weak Linear Correlation:** Little or no linear relationship is observed.

### Pearson Correlation Coefficient

The Pearson correlation coefficient is represented by `r`.

Its value ranges from -1 to +1.

| Correlation | General Interpretation |
|---|---|
| +1 | Perfect positive linear relationship |
| Positive value | Positive linear association |
| 0 | No linear correlation |
| Negative value | Negative linear association |
| -1 | Perfect negative linear relationship |

### Correlation Is Not Causation

Correlation does not prove that one variable causes changes in another.

For example, advertising expenditure and sales may increase together, but other factors could influence both variables.

Further investigation is necessary before making causal claims.

## 6. Grouped Analysis

Grouped analysis calculates metrics for different categories, such as products, regions, customers, or departments.

### Example: Revenue by Product

| Product | Total Revenue |
|---|---:|
| Laptop | ₹160,000 |
| Mouse | ₹7,500 |
| Keyboard | ₹3,000 |
| **Total** | **₹170,500** |

### Example: Revenue by Region

| Region | Total Revenue |
|---|---:|
| South | ₹123,000 |
| North | ₹2,500 |
| East | ₹40,000 |
| West | ₹5,000 |
| **Total** | **₹170,500** |

### Percentage Contribution

Contribution % = (Category Revenue / Total Revenue) × 100

For laptop revenue:

(₹160,000 / ₹170,500) × 100 = 93.84%

**Business Insight:** Laptops contribute approximately 93.84% of the revenue in this sample.

This observation should be investigated further using profit margins, costs, inventory, and customer-demand data.

## 7. Time-Based Analysis

Time-based analysis examines how business metrics change over time.

It can help identify:
- Growth and decline.
- Seasonal patterns.
- Long-term trends.
- Unusual changes.
- Business performance over different periods.

### Month-over-Month Growth

MoM Growth % = [(Current Month - Previous Month) / Previous Month] × 100

Example:

Previous Month Revenue = ₹100,000

Current Month Revenue = ₹120,000

MoM Growth = [(120,000 - 100,000) / 100,000] × 100

**Result: 20% growth**

### Trend vs. Seasonality

- **Trend:** Long-term direction of a metric.
- **Seasonality:** A recurring pattern at a known interval.
- **Irregular Variation:** Unexpected fluctuations.

### Moving Average

A moving average smooths short-term fluctuations.

Three-Month Moving Average = (Current Month + Previous Month + Month Before Previous) / 3

Moving averages can help identify underlying trends, but they may hide sudden changes.

## 8. Data Visualization for EDA

Visualizations help analysts identify patterns and communicate results.

| Visualization | Purpose | Example |
|---|---|---|
| Bar Chart | Compare categories | Revenue by product |
| Histogram | Understand numerical distributions | Distribution of order values |
| Box Plot | Examine spread and potential outliers | Delivery times by region |
| Scatter Plot | Examine relationships between numerical variables | Advertising spend vs. sales |
| Line Chart | Analyze changes over time | Monthly revenue trends |

A good visualization should answer a specific business question and present the information clearly.

## 9. EDA Using Different Tools

### Excel

Useful functions and features:
- `SUM()`
- `AVERAGE()`
- `MEDIAN()`
- `COUNT()`
- `COUNTIF()`
- `SUMIF()`
- PivotTables
- Conditional Formatting
- Charts

### SQL

Example: Revenue by region.

```sql
SELECT
    Region,
    SUM(Revenue) AS Total_Revenue,
    COUNT(*) AS Total_Orders,
    AVG(Revenue) AS Average_Order_Revenue
FROM Sales
GROUP BY Region
ORDER BY Total_Revenue DESC;
```

This query groups transactions by region, calculates revenue and order counts, and sorts the results by total revenue.

### Python with Pandas

```python
import pandas as pd

df = pd.read_csv("sales.csv")

# Inspect the dataset
print(df.head())
print(df.info())
print(df.describe())

# Check missing values
print(df.isnull().sum())

# Summary statistics
print(df["Revenue"].mean())
print(df["Revenue"].median())
print(df["Revenue"].std())

# Revenue by region
print(
    df.groupby("Region")["Revenue"]
      .sum()
      .sort_values(ascending=False)
)
```

### Power BI and DAX

Example DAX measure:

```dax
Total Revenue = SUM(Sales[Revenue])
```

Example average order revenue measure, assuming each row represents one order:

```dax
Average Order Revenue =
DIVIDE(
    [Total Revenue],
    COUNTROWS(Sales),
    0
)
```

Power BI enables interactive exploration through filters, slicers, visuals, and measures.

## 10. Practical Exercises

The following activities help reinforce the concepts covered in Day 13.

- [ ] Calculate total revenue.
- [ ] Calculate mean and median revenue.
- [ ] Identify minimum and maximum revenue.
- [ ] Calculate revenue by product and region.
- [ ] Calculate percentage contribution by product.
- [ ] Create a bar chart showing revenue by product.
- [ ] Create a histogram of order revenue.
- [ ] Investigate potential outliers.
- [ ] Explore relationships between numerical variables.
- [ ] Calculate month-over-month growth using time-based data.
- [ ] Write at least three business insights.
- [ ] Document limitations and possible next steps.

# 11. Key Learnings

After completing Day 13, I learned:

- How to use summary statistics to understand numerical data.
- How to interpret normal, skewed, and uniform distributions.
- How to identify and investigate potential outliers.
- How to interpret correlation without assuming causation.
- How to compare metrics across categories.
- How to analyze trends and changes over time.
- How to select suitable charts for analytical questions.
- How to use Excel, SQL, Python, and Power BI for EDA.
- How to translate numerical results into business insights.