# Day 16: Exploratory Data Analysis (EDA) – Advanced Analysis

## 🎯 Learning Objectives

- Understand univariate, bivariate, and multivariate analysis.
- Learn measures of central tendency and dispersion.
- Understand different types of data distributions.
- Analyze relationships between numerical and categorical variables.
- Understand correlation and its limitations.
- Identify potential outliers using the IQR method.
- Perform EDA using Excel, Python, and Power BI.
- Convert analytical results into actionable business insights.

## 1. Univariate Analysis

Univariate analysis examines one variable at a time to understand its characteristics and distribution.

### Examples
- Analyzing sales values.
- Finding average customer age.
- Identifying the most frequently purchased product.
- Understanding the distribution of employee salaries.

### Measures of Central Tendency

**Mean:** The arithmetic average of all observations.

Formula:

Mean = Sum of all values / Number of observations

**Median:** The middle value after sorting the observations.

**Mode:** The most frequently occurring value.

### Measures of Dispersion

**Range:** Difference between the maximum and minimum values.

Range = Maximum - Minimum

**Variance:** Measures the average squared deviation from the mean, using the appropriate population or sample formula.

**Standard Deviation:** The square root of variance. It describes how spread out the values are around the mean.

### Common Visualizations
- Histogram
- Box plot
- Bar chart
- Density plot

## 2. Bivariate Analysis

Bivariate analysis examines the relationship between two variables.

### Examples
- Sales vs. Quantity
- Advertising Spend vs. Revenue
- City vs. Sales
- Product Category vs. Profit

### Techniques

**Scatter Plot:** Visualizes the relationship between two numerical variables.

**Grouped Analysis:** Compares numerical measures across categories.

**Cross-Tabulation:** Examines combinations of two categorical variables.

### Correlation

Correlation measures the direction and strength of association between two variables, commonly using Pearson's correlation coefficient.

The correlation coefficient ranges from -1 to +1.

| Correlation | Interpretation |
|---|---|
| +1 | Perfect positive linear relationship |
| Positive value | Positive linear association |
| 0 | No linear association |
| Negative value | Negative linear association |
| -1 | Perfect negative linear relationship |

**Important:** Correlation does not imply causation. Two variables may be associated without one causing the other.

## 3. Multivariate Analysis

Multivariate analysis examines three or more variables together to understand more complex patterns.

### Example

An e-commerce company may analyze:

- Advertising Spend
- Website Visitors
- Orders
- Discount Percentage
- Revenue

This analysis can help the business investigate campaign performance, customer conversion, and sales patterns.

### Common Techniques
- Correlation Matrix
- Grouped Scatter Plot
- Bubble Chart
- Comparative Box Plots
- Regression Analysis

The choice of technique depends on the business question and the types of variables available.

## 4. Understanding Data Distributions

A distribution describes how values are spread across a dataset.

### Types of Distributions

**Symmetric Distribution:** Values are distributed approximately evenly around the center.

**Right-Skewed Distribution:** The distribution has a longer tail toward larger values. High-value transactions may pull the mean above the median.

**Left-Skewed Distribution:** The distribution has a longer tail toward smaller values. Low values may pull the mean below the median.

Understanding distributions helps identify unusual patterns and select appropriate summary statistics.

## 5. Outlier Detection Using IQR

An outlier is an observation that differs substantially from the general pattern of the data.

The Interquartile Range (IQR) method helps identify potential outliers.

IQR = Q3 - Q1

Lower Fence = Q1 - 1.5 × IQR

Upper Fence = Q3 + 1.5 × IQR

Where:
- Q1 = First quartile (25th percentile)
- Q3 = Third quartile (75th percentile)
- IQR = Spread of the middle 50% of observations

Values outside these fences are flagged as potential outliers.

### Handling Outliers

1. Investigate unusual values.
2. Check for data-entry or measurement errors.
3. Verify the business context.
4. Correct confirmed errors when the correct values are known.
5. Retain legitimate observations or use an appropriate treatment.
6. Document any changes made.

Outliers should not be automatically deleted because they may represent genuine business events.

## 6. EDA Using Excel

Excel provides useful formulas for statistical analysis.

Assuming sales values are stored in cells `B2:B101`:

| Objective | Excel Formula |
|---|---|
| Mean | `=AVERAGE(B2:B101)` |
| Median | `=MEDIAN(B2:B101)` |
| Mode | `=MODE.SNGL(B2:B101)` |
| Minimum | `=MIN(B2:B101)` |
| Maximum | `=MAX(B2:B101)` |
| Sample Standard Deviation | `=STDEV.S(B2:B101)` |
| First Quartile | `=QUARTILE.INC(B2:B101,1)` |
| Third Quartile | `=QUARTILE.INC(B2:B101,3)` |

### Practical Activities
- Calculate descriptive statistics.
- Create a histogram.
- Create a box-and-whisker chart.
- Use PivotTables to compare sales by city.
- Compare average sales and total sales across categories.

## 7. EDA Using Python

Python and Pandas help automate exploratory data analysis.

### Sample Code

```python
import pandas as pd
import matplotlib.pyplot as plt

data = {
    "City": [
        "Hyderabad", "Chennai", "Bengaluru",
        "Hyderabad", "Chennai", "Bengaluru"
    ],
    "Sales": [50000, 30000, 45000, 40000, 35000, 55000],
    "Quantity": [5, 3, 4, 4, 3, 6]
}

df = pd.DataFrame(data)

# Explore the dataset
print(df.head())
print(df.info())
print(df.describe())

# Univariate analysis
print("Mean:", df["Sales"].mean())
print("Median:", df["Sales"].median())
print("Standard Deviation:", df["Sales"].std())

# Frequency analysis
print(df["City"].value_counts())

# Bivariate analysis
print(df.groupby("City")["Sales"].mean())

# Correlation analysis
print(df[["Sales", "Quantity"]].corr())

# Visualize sales distribution
df["Sales"].hist()
plt.xlabel("Sales")
plt.ylabel("Frequency")
plt.title("Sales Distribution")
plt.show()

# Compare average sales by city
df.groupby("City")["Sales"].mean().plot(kind="bar")
plt.ylabel("Average Sales")
plt.title("Average Sales by City")
plt.show()
```

### Key Python Functions

| Function | Purpose |
|---|---|
| `head()` | Displays the first rows |
| `info()` | Displays column types and non-null counts |
| `describe()` | Generates descriptive statistics |
| `mean()` | Calculates the arithmetic mean |
| `median()` | Calculates the median |
| `value_counts()` | Counts occurrences of categories |
| `groupby()` | Groups observations for analysis |
| `corr()` | Calculates correlations |
| `hist()` | Creates a histogram |

## 8. EDA Using Power BI

Power BI helps present EDA findings through interactive reports and dashboards.

### Recommended Visuals

| Visual | Purpose |
|---|---|
| Card | Display total sales and order counts |
| Bar Chart | Compare sales by city or product |
| Histogram | Examine numerical distributions |
| Scatter Chart | Explore relationships between numerical variables |
| Matrix | Compare measures across multiple categories |
| Slicer | Filter data by date, city, or product |

### Example DAX Measures

```dax
Total Sales =
SUM(SalesData[Sales])
```

```dax
Total Orders =
DISTINCTCOUNT(SalesData[OrderID])
```

```dax
Average Order Value =
DIVIDE([Total Sales], [Total Orders], 0)
```

These measures recalculate according to the current filter context, assuming the data model is configured correctly.

## 9. Professional EDA Workflow

A structured EDA process includes:

1. Define the business question.
2. Understand the dataset and its columns.
3. Validate data quality.
4. Perform univariate analysis.
5. Perform bivariate and multivariate analysis.
6. Investigate distributions and potential outliers.
7. Visualize important patterns.
8. Validate findings.
9. Communicate business insights and recommendations.

## 10. Key Takeaways

- Univariate analysis examines one variable.
- Bivariate analysis examines two variables.
- Multivariate analysis examines three or more variables.
- Mean, median, and mode describe central tendency.
- Range, variance, and standard deviation describe dispersion.
- Correlation measures association, not causation.
- IQR is a useful method for flagging potential outliers.
- Excel, Python, and Power BI support different stages of EDA.
- Business insights should be supported by validated evidence.

## Business Applications

Exploratory Data Analysis is useful for:

- Sales performance analysis
- Customer behavior analysis
- Marketing campaign evaluation
- Financial reporting
- Inventory management
- Employee performance analysis
- Identifying data-quality issues

