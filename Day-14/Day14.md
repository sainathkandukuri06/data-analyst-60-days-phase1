# Day 14: Exploratory Data Analysis (EDA) – Patterns, Relationships & Business Insights

# Learning Objectives

- Understand patterns and trends in datasets.
- Analyze relationships between variables.
- Learn correlation and covariance.
- Detect and investigate outliers.
- Understand data distributions.
- Perform segment and time-based analysis.
- Choose appropriate charts for data exploration.
- Convert analytical findings into business insights.
- Practice EDA concepts using Excel and Power BI.


# 1. Exploratory Data Analysis (EDA)

Exploratory Data Analysis is the process of examining a dataset to understand its structure, identify patterns, discover relationships, and detect unusual observations before drawing conclusions.

# Why is EDA important?

- Helps identify data quality issues.
- Reveals trends and patterns.
- Detects potential outliers.
- Helps understand relationships between variables.
- Supports better business decisions.
- Helps determine which visualizations and further analyses are useful.

# EDA Workflow

1. Collect data.
2. Clean and prepare data.
3. Explore the dataset using statistical measures.
4. Identify patterns, trends, and relationships.
5. Visualize findings.
6. Generate insights and communicate limitations.

---

## 2. Patterns and Trends

A pattern is a recognizable behavior in data, while a trend represents the general direction of change over time.

### Types of Patterns

- **Upward Trend:** Values generally increase over time.
- **Downward Trend:** Values generally decrease over time.
- **Seasonal Pattern:** Values repeat at particular times or intervals.
- **Stable Pattern:** Values remain within a relatively consistent range.

### Percentage Growth Formula

Percentage Growth = ((New Value - Old Value) / Old Value) × 100

**Example:**

Previous month sales = ₹20,000  
Current month sales = ₹24,000

Growth = ((24,000 - 20,000) / 20,000) × 100

**Result: 20% growth**

### Excel Formula

```excel
=(B3-B2)/B2
```

Format the result as a percentage.

---

## 3. Relationships Between Variables

A relationship exists when changes in one variable are associated with changes in another.

Examples:

- Advertising Spend and Sales Revenue
- Product Price and Quantity Sold
- Customer Age and Spending
- Discount Percentage and Profit Margin

### Types of Relationships

**Positive Relationship:** Both variables tend to increase together.

**Negative Relationship:** One variable tends to decrease when the other increases.

**No Clear Linear Relationship:** There is no obvious straight-line association between the variables.

### Scatter Plot

A scatter plot displays pairs of numerical observations and helps identify relationships, clusters, and unusual observations.

**Important:** Correlation does not prove causation. Other factors may explain the observed relationship.

---

## 4. Correlation

Correlation measures the strength and direction of the linear relationship between two numerical variables when using Pearson's correlation coefficient.

The Pearson correlation coefficient ranges from -1 to +1.

### Interpretation

| Correlation | Interpretation |
|---|---|
| +1.0 | Perfect positive linear relationship |
| +0.8 | Strong positive linear association |
| +0.3 | Weak positive linear association |
| 0.0 | No linear correlation |
| -0.3 | Weak negative linear association |
| -0.8 | Strong negative linear association |
| -1.0 | Perfect negative linear relationship |

These strength labels are general guidelines and depend on the data and business context.

### Pearson Correlation Formula

r = Cov(X, Y) / (SD(X) × SD(Y))

Where:

- `r` = Correlation coefficient
- `Cov(X, Y)` = Covariance between X and Y
- `SD(X)` = Standard deviation of X
- `SD(Y)` = Standard deviation of Y

### Excel Function

```excel
=CORREL(A2:A6,B2:B6)
```

A result close to +1 indicates a strong positive linear association. A result close to -1 indicates a strong negative linear association.

Correlation alone does not establish a causal relationship.

---

## 5. Covariance

Covariance measures how two variables vary together.

- **Positive Covariance:** Variables tend to move in the same direction.
- **Negative Covariance:** Variables tend to move in opposite directions.
- **Covariance Near Zero:** Little linear co-movement is detected by the measure.

### Excel Function

```excel
=COVARIANCE.S(A2:A100,B2:B100)
```

Use `COVARIANCE.S` for sample data.

For population data:

```excel
=COVARIANCE.P(A2:A100,B2:B100)
```

### Covariance vs. Correlation

| Feature | Covariance | Correlation |
|---|---|---|
| Purpose | Measures joint variation | Measures standardized linear association |
| Value Range | Not fixed | -1 to +1 |
| Units | Depends on the variables | Unitless |
| Comparability | Difficult across different scales | Generally easier |
| Excel Function | `COVARIANCE.S` | `CORREL` |

---

## 6. Outlier Detection

An outlier is an observation that is unusually far from other values in a dataset.

Example:

`500, 550, 600, 620, 580, 610, 590, 8000`

The value `8000` is much larger than the other observations and should be investigated.

Possible reasons include:

- Data-entry errors
- Duplicate transactions
- Genuine high-value transactions
- Unusual customer behavior
- Different customer segments

**Important:** An outlier is not automatically an error. Investigate it before removing or modifying the observation.

### Method 1: Interquartile Range (IQR)

IQR = Q3 - Q1

Where:

- `Q1` = First quartile (25th percentile)
- `Q3` = Third quartile (75th percentile)

Lower Fence = Q1 - 1.5 × IQR

Upper Fence = Q3 + 1.5 × IQR

Values outside these fences are commonly flagged as potential outliers.

### Excel Functions

```excel
=QUARTILE.INC(A2:A100,1)
```

```excel
=QUARTILE.INC(A2:A100,3)
```

Calculate the IQR by subtracting Q1 from Q3.

### Method 2: Z-Score

Z-score = (Observation - Mean) / Standard Deviation

A z-score indicates how many standard deviations an observation lies from the mean.

An absolute z-score greater than 3 is sometimes used to flag unusual observations, although the rule is not suitable for every distribution.

---

## 7. Distribution Analysis

A distribution describes how frequently different values occur and how numerical observations are spread.

### Common Distribution Types

**Symmetric Distribution:** Values are distributed approximately evenly around the center.

**Right-Skewed Distribution:** The distribution has a longer tail toward higher values.

**Left-Skewed Distribution:** The distribution has a longer tail toward lower values.

### Important Statistical Measures

- **Mean:** Arithmetic average.
- **Median:** Middle value after sorting.
- **Mode:** Most frequently occurring value.
- **Range:** Maximum minus minimum.
- **Variance:** Measure of squared deviations from the mean.
- **Standard Deviation:** Measure of spread around the mean.
- **IQR:** Spread of the middle 50% of observations.

For strongly skewed data, the median may describe a typical observation better than the mean.

---

## 8. Segment Analysis

Segment analysis divides a dataset into meaningful groups to compare performance.

Examples:

- Revenue by region
- Sales by product category
- Profit by customer segment
- Orders by sales channel
- Customer retention by subscription type

### Excel Functions

Calculate total revenue:

```excel
=SUM(B2:B100)
```

Calculate revenue for a specific region:

```excel
=SUMIF(A2:A100,"South",B2:B100)
```

Here, column A contains the region and column B contains revenue.

### Business Questions

- Which region generates the highest revenue?
- Which category sells the most units?
- Which customer group generates the most profit?
- Are some segments performing below expectations?

Revenue alone does not measure profitability. Consider costs, discounts, and margins when evaluating business performance.

---

## 9. Time-Based Analysis

Time-based analysis investigates how a metric changes over time.

Examples:

- Daily sales
- Weekly orders
- Monthly revenue
- Quarterly profit
- Year-over-year growth

### Month-over-Month Growth Formula

MoM Growth = ((Current Month - Previous Month) / Previous Month) × 100

**Example:**

Previous month revenue = ₹150,000  
Current month revenue = ₹180,000

MoM Growth = ((180,000 - 150,000) / 150,000) × 100

**Result: 20% growth**

The formula requires care when the previous period is zero or negative.

### Useful Visualizations

- Line charts for trends
- Column charts for period comparisons
- Heatmaps for recurring time patterns
- Moving averages for smoothing short-term fluctuations

---

## 10. Choosing the Right Visualization

| Chart | Purpose | Example |
|---|---|---|
| Histogram | Understand a numerical distribution | Customer Age |
| Scatter Plot | Investigate relationships | Advertising Spend vs. Revenue |
| Line Chart | Analyze changes over time | Monthly Sales |
| Box Plot | Compare distributions and flag potential outliers | Order Amounts by Region |
| Bar Chart | Compare categories | Revenue by Product |
| Heatmap | Identify patterns across two dimensions | Sales by Day and Hour |

Always select a visualization based on the analytical question.

---

## 11. Practical Sales Analysis Example

Consider the following sample transactions:

| Order | Region | Product | Quantity | Unit Price |
|---|---|---|---:|---:|
| 101 | South | Laptop | 2 | 40000 |
| 102 | North | Mouse | 10 | 500 |
| 103 | South | Keyboard | 5 | 1500 |
| 104 | West | Laptop | 1 | 40000 |
| 105 | East | Mouse | 8 | 500 |
| 106 | South | Laptop | 3 | 40000 |

### Step 1: Calculate Revenue

Revenue = Quantity × Unit Price

For Order 101:

2 × 40000 = ₹80,000

### Step 2: Calculate Total Revenue

| Order | Revenue |
|---|---:|
| 101 | ₹80,000 |
| 102 | ₹5,000 |
| 103 | ₹7,500 |
| 104 | ₹40,000 |
| 105 | ₹4,000 |
| 106 | ₹120,000 |
| **Total** | **₹256,500** |

### Step 3: Analyze Regional Revenue

South region revenue:

₹80,000 + ₹7,500 + ₹120,000 = ₹207,500

South's share of total revenue:

(207,500 / 256,500) × 100 ≈ 80.9%

### Step 4: Generate Business Insights

- Total revenue from the six sample transactions is ₹256,500.
- The South region contributes approximately 80.9% of the sample revenue.
- Laptop transactions account for a substantial share of revenue.
- The largest transaction should be validated rather than automatically removed as an outlier.
- A larger dataset is required to determine whether the observed patterns continue over time.

---

## 12. Excel Practice

Useful Excel functions for EDA:

| Function | Purpose |
|---|---|
| `SUM()` | Calculate totals |
| `AVERAGE()` | Calculate the mean |
| `MEDIAN()` | Calculate the median |
| `MIN()` | Find the minimum |
| `MAX()` | Find the maximum |
| `CORREL()` | Calculate Pearson correlation |
| `COVARIANCE.S()` | Calculate sample covariance |
| `QUARTILE.INC()` | Calculate quartiles |
| `SUMIF()` | Calculate totals for a condition |
| `COUNTIF()` | Count observations meeting a condition |

### Excel Tasks

1. Calculate revenue for each transaction.
2. Find total and average revenue.
3. Compare revenue by region.
4. Create a monthly sales trend chart.
5. Build a scatter plot for advertising spend versus revenue.
6. Identify and investigate potential outliers.
7. Write three business insights based on the findings.

---

## 13. Power BI Practice

Power BI can help explore data interactively and communicate analytical findings.

### Suggested Visuals

- Card: Total Revenue
- Bar Chart: Revenue by Region
- Column Chart: Revenue by Product Category
- Line Chart: Monthly Revenue Trend
- Scatter Chart: Advertising Spend vs. Revenue
- Slicers: Region, Product Category, and Date

### DAX Measure: Total Revenue

```dax
Total Revenue =
SUMX(
    Sales,
    Sales[Quantity] * Sales[Unit Price]
)
```

This measure calculates revenue for each row and adds the results.

If a valid revenue column already exists, use:

```dax
Total Revenue =
SUM(Sales[Revenue])
```

Replace the table and column names with the names in your own dataset.

### Power BI Tasks

1. Import the sales dataset.
2. Verify data types and relationships.
3. Create a total revenue measure.
4. Compare performance across regions and categories.
5. Explore monthly trends.
6. Investigate relationships using a scatter chart.
7. Add slicers for interactive analysis.
8. Document the findings and limitations.


# 14. Day 14 Practical Assignment

Create a dataset containing at least 30–50 sales records with the following columns:

- Order Date
- Region
- Product Category
- Quantity
- Unit Price
- Advertising Spend

# Checklist

- [ ] Calculate transaction revenue.
- [ ] Find total revenue and average order revenue.
- [ ] Identify the highest-performing region.
- [ ] Create a monthly sales trend chart.
- [ ] Explore advertising spend versus revenue.
- [ ] Flag and investigate potential outliers.
- [ ] Write three evidence-based business insights.
- [ ] Document one limitation of the analysis.
- [ ] Save the work in the Day 14 GitHub folder.


# 15. Key Learnings

By completing Day 14, I learned:

- How to perform exploratory analysis beyond basic summaries.
- How to recognize patterns and trends.
- How to investigate relationships between variables.
- How to interpret correlation and covariance.
- How to detect potential outliers using IQR and z-scores.
- How to understand distributions.
- How to compare business segments.
- How to perform time-based analysis.
- How to select charts for specific analytical questions.
- How to use Excel and Power BI for EDA.
- How to communicate findings with appropriate limitations.
