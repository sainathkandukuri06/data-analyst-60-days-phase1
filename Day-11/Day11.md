# Day 11: Exploratory Data Analysis (EDA) — Advanced Analysis & Business Insights

# Learning Objectives

By the end of Day 11, I learned:

- What Exploratory Data Analysis (EDA) is and why it matters.
- How to calculate and interpret descriptive statistics.
- How to understand data distributions.
- How to analyze trends and percentage changes.
- How to identify relationships between variables.
- How to detect and investigate outliers.
- How to compare business performance across segments.
- How to convert analytical findings into business insights.
- How to apply EDA concepts using Excel and Power BI.

# 1. What Is Exploratory Data Analysis (EDA)?

Exploratory Data Analysis is the process of examining a dataset to understand its structure, quality, patterns, relationships, and unusual observations before drawing conclusions.

# Why Is EDA Important?

- Helps identify missing values and data-quality problems.
- Provides an overview of the dataset.
- Reveals patterns, trends, and relationships.
- Helps identify potential outliers.
- Supports better business decision-making.
- Helps determine which visualizations and metrics are useful.

# Typical EDA Workflow

1. Understand the dataset and its columns.
2. Check data types, missing values, and duplicates.
3. Calculate descriptive statistics.
4. Explore distributions and outliers.
5. Analyze trends and relationships.
6. Compare performance across groups.
7. Communicate findings and recommendations.

**Key takeaway:** EDA helps analysts understand what the data contains before making business conclusions.

# 2. Descriptive Statistics

Descriptive statistics summarize numerical data using meaningful measurements.

# 2.1 Mean

The mean is the average of all observations.

**Formula:**

Mean = Sum of all values / Number of observations

Example:

Daily sales = ₹100, ₹200, ₹300, ₹400, ₹500

Mean = ₹1,500 / 5 = ₹300

**Business applications:**
- Average order value
- Average salary
- Average monthly revenue
- Average delivery time

**Limitation:** The mean can be affected by extreme values.

# 2.2 Median

The median is the middle value after sorting observations in ascending order.

Example:

10, 20, 30, 40, 50

Median = 30

For an even number of observations:

10, 20, 30, 40

Median = (20 + 30) / 2 = 25

**Business applications:**
- Typical customer spending
- Salary analysis
- Delivery-time analysis

The median is useful when data is skewed or contains extreme values.

### 2.3 Mode

The mode is the most frequently occurring value.

Example:

2, 3, 3, 3, 5, 7

Mode = 3

**Business applications:**
- Most popular product
- Most common payment method
- Most frequent order quantity

### 2.4 Range

Range measures the difference between the maximum and minimum values.

**Formula:**

Range = Maximum − Minimum

Example:

100, 200, 300, 400, 500

Range = 500 − 100 = 400

### 2.5 Standard Deviation

Standard deviation measures how much observations vary around their mean.

- Low standard deviation: values are relatively close to the mean.
- High standard deviation: values are more spread out.

Population standard deviation:

σ = √[Σ(xᵢ − μ)² / N]

Sample standard deviation:

s = √[Σ(xᵢ − x̄)² / (n − 1)]

Where:
- xᵢ = individual observation
- μ = population mean
- x̄ = sample mean
- N = population size
- n = sample size

**Business applications:**
- Measuring sales variability
- Comparing store performance consistency
- Analyzing delivery-time variation

---

## 3. Understanding Data Distributions

A data distribution describes how observations are spread across different values.

### 3.1 Symmetric Distribution

Values are distributed relatively evenly around the center.

For a perfectly symmetric distribution, the mean and median are equal.

### 3.2 Right-Skewed Distribution

A right-skewed distribution has a long tail toward higher values.

The mean is often greater than the median.

Example: Customer spending, where a few customers make very large purchases.

### 3.3 Left-Skewed Distribution

A left-skewed distribution has a long tail toward lower values.

The mean is often less than the median.

Example: Exam scores where most students score highly but a few score very low.

### How to Analyze a Distribution

1. Calculate the mean and median.
2. Find the minimum and maximum.
3. Create a histogram.
4. Look for clusters and long tails.
5. Investigate unusual values.

---

## 4. Trend Analysis

Trend analysis examines how a business metric changes over time.

Examples include daily sales, monthly revenue, annual profit, and customer growth.

### 4.1 Absolute Change

**Formula:**

Change = Current Value − Previous Value

Example:

January revenue = ₹1,00,000  
February revenue = ₹1,10,000

Change = ₹1,10,000 − ₹1,00,000 = ₹10,000

### 4.2 Percentage Change

**Formula:**

Percentage Change = [(Current Value − Previous Value) / Previous Value] × 100

Example:

Percentage Change = [(110000 − 100000) / 100000] × 100

Percentage Change = 10%

Revenue increased by 10%.

### 4.3 Moving Average

A moving average smooths short-term fluctuations to make the underlying trend easier to identify.

Example:

January = ₹1,00,000  
February = ₹1,10,000  
March = ₹1,05,000

Three-month moving average:

(100000 + 110000 + 105000) / 3 = ₹1,05,000

### 4.4 Trend vs. Seasonality

- **Trend:** Long-term direction of a metric.
- **Seasonality:** A pattern that repeats at regular intervals.
- **Random fluctuation:** Variation without an obvious repeatable pattern.

Example: Retail sales may increase during festival seasons every year.

---

## 5. Relationship Analysis

Relationship analysis examines whether variables are associated with each other.

Example: An analyst studies the relationship between advertising expenditure and sales revenue.

### 5.1 Correlation

Correlation measures the strength and direction of a linear relationship between two numerical variables.

The Pearson correlation coefficient ranges from -1 to +1.

| Correlation | Interpretation |
|---|---|
| Near +1 | Strong positive linear relationship |
| Near 0 | Little or no linear relationship |
| Near -1 | Strong negative linear relationship |

### 5.2 Correlation Formula

r = Cov(X, Y) / (sₓ × sᵧ)

Where:
- X and Y are numerical variables.
- Cov(X, Y) is their covariance.
- sₓ and sᵧ are their standard deviations.

### 5.3 Correlation vs. Causation

Correlation does not prove causation.

Example: Sales and advertising expenditure may increase together, but sales may also be influenced by seasonality, discounts, product availability, or customer demand.

Additional evidence is required to establish whether advertising caused the increase.

### 5.4 Scatter Plots

Scatter plots help visualize relationships between two numerical variables.

They can reveal:
- Positive or negative associations
- Possible outliers
- Clusters
- Linear or nonlinear patterns

---

## 6. Outlier Analysis

An outlier is an observation that differs substantially from the overall pattern of the dataset.

Example:

₹500, ₹600, ₹650, ₹700, ₹750, ₹800, ₹15,000

The ₹15,000 observation may be an outlier.

However, an outlier is not automatically an error. It may represent a genuine transaction or a data-quality problem.

### 6.1 Interquartile Range (IQR)

IQR measures the spread of the middle 50% of observations.

**Formula:**

IQR = Q3 − Q1

Where:
- Q1 = 25th percentile
- Q3 = 75th percentile

### 6.2 IQR Outlier Boundaries

Lower Bound = Q1 − 1.5 × IQR

Upper Bound = Q3 + 1.5 × IQR

Observations outside these boundaries are commonly flagged as potential outliers.

### 6.3 How to Handle Outliers

1. Identify unusual observations.
2. Check the original source.
3. Verify units and data-entry accuracy.
4. Determine whether the observation is legitimate.
5. Decide whether to retain, correct, exclude, or analyze it separately.

**Important:** Never remove outliers without understanding their meaning and impact on the analysis.

---

## 7. Segmentation Analysis

Segmentation divides a dataset into meaningful groups for comparison.

Common segmentation categories include:

- Region
- Product category
- Customer type
- Sales channel
- Time period

### Example: Revenue by Region

| Region | Net Revenue |
|---|---:|
| South | ₹86,300 |
| North | ₹8,000 |
| East | ₹39,000 |
| Total | ₹1,33,300 |

South generates the highest revenue in this example.

### Revenue Contribution Formula

Revenue Share = (Regional Revenue / Total Revenue) × 100

South Revenue Share:

(86300 / 133300) × 100 ≈ 64.74%

South contributes approximately 64.74% of the total net revenue.

Further analysis is required to understand the reasons for this performance and whether the region is also more profitable.

---

## 8. Practice Sales Dataset

The following dataset can be used to practice EDA.

| Order ID | Region | Product | Units | Price per Unit | Discount | Net Revenue |
|---|---|---|---:|---:|---:|---:|
| 101 | South | Laptop | 2 | ₹40,000 | ₹2,000 | ₹78,000 |
| 102 | North | Mouse | 10 | ₹500 | ₹0 | ₹5,000 |
| 103 | South | Keyboard | 5 | ₹1,000 | ₹500 | ₹4,500 |
| 104 | East | Laptop | 1 | ₹40,000 | ₹1,000 | ₹39,000 |
| 105 | North | Keyboard | 3 | ₹1,000 | ₹0 | ₹3,000 |
| 106 | South | Mouse | 8 | ₹500 | ₹200 | ₹3,800 |

**Net Revenue Formula:**

Net Revenue = (Units × Price per Unit) − Discount

Total Net Revenue = ₹1,33,300

Note: Discount represents the total discount for each order.

---

## 9. EDA Using Microsoft Excel

Excel can be used to perform descriptive analysis, grouping, calculations, and visualization.

### Useful Excel Functions

| Function | Purpose |
|---|---|
| SUM() | Calculates the total |
| AVERAGE() | Calculates the mean |
| MEDIAN() | Calculates the median |
| MODE.SNGL() | Finds the most frequent value |
| MIN() | Finds the minimum |
| MAX() | Finds the maximum |
| STDEV.S() | Calculates sample standard deviation |
| COUNT() | Counts numerical values |

Example formulas, assuming Net Revenue is in cells G2:G7:

```excel
=SUM(G2:G7)
=AVERAGE(G2:G7)
=MEDIAN(G2:G7)
=MIN(G2:G7)
=MAX(G2:G7)
=STDEV.S(G2:G7)
=COUNT(G2:G7)
```

### Excel EDA Workflow

1. Convert the dataset into a table using Ctrl + T.
2. Check missing values and duplicates.
3. Review column names and data types.
4. Calculate summary statistics.
5. Create a PivotTable to compare revenue by region.
6. Use charts to identify patterns.
7. Write observations and recommendations.

### Recommended Visualizations

| Chart | Use |
|---|---|
| Bar chart | Compare revenue across regions or products |
| Line chart | Analyze changes over time |
| Histogram | Understand data distributions |
| Scatter plot | Explore relationships between numerical variables |
| Box plot | Compare distributions and investigate potential outliers |

---

## 10. EDA Using Power BI

Power BI can be used to turn exploratory analysis into interactive reports.

### Workflow

1. Import the dataset.
2. Clean and transform data using Power Query.
3. Create measures using DAX.
4. Build charts, cards, and tables.
5. Add slicers to explore regions and products.
6. Interpret the results and communicate business insights.

### Example DAX Measure

```dax
Total Revenue =
SUMX(
    Sales,
    Sales[Units] * Sales[Price]
        - Sales[Discount]
)
```

This measure calculates net revenue across the rows in the Sales table, subject to the current filter context.


# 11. Converting Analysis into Business Insights

A professional Data Analyst must explain the meaning of analytical findings.

A useful structure is:

# Observation
What does the data show?

# Interpretation
What might explain the pattern?

# Recommendation
What should the business investigate or do next?

**Example:**

- Observation: South contributes approximately 64.74% of net revenue.
- Interpretation: Laptop sales contribute substantially to revenue in this dataset.
- Recommendation: Investigate product mix, costs, margins, and regional demand to better understand the performance.

Always separate confirmed observations from possible explanations.

# 12. Day 11 Practical Tasks

- [ ] Calculate total net revenue.
- [ ] Calculate average revenue per order.
- [ ] Find the highest and lowest revenue orders.
- [ ] Calculate revenue contribution by region.
- [ ] Create a bar chart showing revenue by region.
- [ ] Calculate percentage change between two periods using a separate time-based dataset.
- [ ] Identify potential outliers and explain how to investigate them.
- [ ] Write three observations based on the sales data.
- [ ] Write one business recommendation.
- [ ] Explain what additional information is needed to validate the recommendation.

---

## 13. Key Learnings

| Concept | Key Learning |
|---|---|
| EDA | Explore data before drawing conclusions |
| Mean | Average of observations |
| Median | Middle value of ordered observations |
| Mode | Most frequent value |
| Range | Difference between maximum and minimum |
| Standard Deviation | Measures variation around the mean |
| Distribution | Describes the spread and shape of values |
| Trend Analysis | Examines changes over time |
| Correlation | Measures linear association between numerical variables |
| Outlier Analysis | Identifies unusual observations for investigation |
| Segmentation | Compares performance across groups |
| Business Insights | Converts evidence into useful interpretations and next steps |

---

## 14. Final Summary

Day 11 strengthened my understanding of Exploratory Data Analysis and its role in professional data analytics.

I learned how to summarize numerical data, understand distributions, analyze trends, explore relationships, investigate outliers, compare segments, and communicate findings using Excel and Power BI.

EDA is not just about calculating numbers. It is about asking meaningful questions, examining evidence, understanding limitations, and helping businesses make better decisions.

**Next:** Day 12 — Data Visualization Principles and Choosing the Right Chart.

---

**Challenge:** 60-Day Data Analyst Challenge  
**Phase:** Phase 1 — Foundations  
**Day Completed:** 11  
**Topics:** EDA, Descriptive Statistics, Distributions, Trend Analysis, Correlation, Outliers, Segmentation, Excel, Power BI
