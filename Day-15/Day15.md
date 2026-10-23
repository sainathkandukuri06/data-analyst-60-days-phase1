# Day 15: Exploratory Data Analysis (EDA) — Bivariate Analysis

# Learning Objectives

- Understand the concept and importance of Bivariate Analysis.
- Differentiate between Univariate, Bivariate, and Multivariate Analysis.
- Identify numerical and categorical variables.
- Analyze relationships between two numerical variables.
- Understand correlation and its interpretation.
- Compare numerical data across different categories.
- Analyze relationships between two categorical variables.
- Create scatter plots and cross-tabulations using Python.
- Generate meaningful business insights from data.

---

## 1. What Is Bivariate Analysis?

**Bivariate Analysis** is the process of analyzing two variables together to identify relationships, patterns, associations, or differences.

The term consists of:
- **Bi:** Two
- **Variate:** Variable

### Example

An e-commerce company wants to understand whether advertising expenditure is associated with sales revenue.

- Variable 1: Advertising Spend
- Variable 2: Sales Revenue

By analyzing these variables together, the company can investigate whether higher advertising expenditure is associated with higher sales.

### Importance of Bivariate Analysis

- Helps identify relationships between variables.
- Supports data-driven business decisions.
- Helps identify patterns and unusual observations.
- Enables comparison between customer groups.
- Provides insights for further statistical analysis.

---

## 2. Types of Data Analysis

| Analysis Type | Description | Example |
|---|---|---|
| Univariate Analysis | Analyzes one variable | Average employee salary |
| Bivariate Analysis | Analyzes two variables | Advertising Spend vs. Sales |
| Multivariate Analysis | Analyzes three or more variables | Experience, Education, and Salary |

---

## 3. Understanding Variable Types

### A. Numerical Variables

Numerical variables represent measurable or countable quantities.

Examples:
- Age
- Salary
- Revenue
- Profit
- Product Price
- Number of Orders

Numerical variables can be classified as:

- **Discrete:** Countable values, such as the number of orders.
- **Continuous:** Measurable values, such as weight or delivery time.

### B. Categorical Variables

Categorical variables represent groups or labels.

Examples:
- Product Category
- Payment Method
- Customer Segment
- City
- Shipping Method

Categorical variables may be nominal (without a natural order) or ordinal (with a meaningful order).

---

## 4. Numerical vs. Numerical Analysis

When both variables are numerical, we analyze whether changes in one variable are associated with changes in another.

### Example

- Advertising Spend
- Sales Revenue

### A. Scatter Plot

A scatter plot represents the relationship between two numerical variables using individual data points.

- X-axis: Independent or explanatory variable.
- Y-axis: Dependent or response variable.
- Each point: One observation.

Common patterns include:

1. **Positive Relationship:** Both variables tend to increase together.
2. **Negative Relationship:** One variable tends to decrease as the other increases.
3. **No Clear Linear Relationship:** No obvious linear pattern exists.

A scatter plot can also help identify outliers, clusters, and nonlinear relationships.

### B. Correlation

Correlation measures the direction and strength of a linear relationship between two numerical variables.

The Pearson correlation coefficient is represented by `r`.

Its value ranges from -1 to +1.

| Correlation Value | Interpretation |
|---|---|
| +1 | Perfect positive linear correlation |
| Close to +1 | Strong positive linear correlation |
| Close to 0 | Weak or no linear correlation |
| Close to -1 | Strong negative linear correlation |
| -1 | Perfect negative linear correlation |

The interpretation of weak, moderate, and strong correlation depends on the context and data.

### Pearson Correlation Formula

`r = Cov(X, Y) / (σX × σY)`

Where:
- `Cov(X, Y)` = Covariance between X and Y.
- `σX` = Standard deviation of X.
- `σY` = Standard deviation of Y.

### Important Concept: Correlation Is Not Causation

Correlation does not prove that one variable causes another.

For example, ice cream sales and swimming-related accidents may both increase during summer because of warmer weather and increased outdoor activity.

A third variable may influence both observed variables.

Therefore, analysts must consider other factors before making causal conclusions.

---

## 5. Categorical vs. Numerical Analysis

This analysis compares numerical values across different categories.

### Example

Comparing sales revenue across product categories:

| Product Category | Average Order Value |
|---|---:|
| Electronics | ₹4,500 |
| Clothing | ₹1,800 |
| Furniture | ₹7,200 |
| Books | ₹650 |

These are illustrative values.

### Common Techniques

**1. Grouped Summary Statistics**

Calculate the following for each category:
- Count
- Mean
- Median
- Sum
- Minimum and maximum

**2. Box Plot**

A box plot helps compare distributions across categories by showing:
- Median
- Quartiles
- Spread of the central 50% of observations
- Potential outliers

### Business Questions

- Which category has the highest average order value?
- Which category generates the highest total revenue?
- Which category has the greatest variation?
- Are there extreme values affecting the average?

Remember that average order value and total revenue are different business metrics.

---

## 6. Categorical vs. Categorical Analysis

This analysis examines the relationship between two categorical variables.

### Example

An e-commerce company wants to understand the payment preferences of different customer segments.

Variables:
- Customer Segment
- Payment Method

### Cross-Tabulation

A cross-tabulation counts the occurrences of combinations of categorical variables.

Example:

| Customer Segment | UPI | Card | Cash on Delivery |
|---|---:|---:|---:|
| New | 120 | 60 | 90 |
| Regular | 180 | 110 | 70 |
| Premium | 80 | 140 | 10 |

These values are illustrative.

### Benefits

- Identifies common combinations of categories.
- Helps compare customer behavior.
- Supports customer segmentation.
- Reveals differences in payment preferences.

### Counts vs. Percentages

Raw counts can be misleading when groups have different sizes.

Formula:

`Percentage = (Category Count / Relevant Group Total) × 100`

Row percentages compare category distributions within each row group. Column percentages compare the composition of each column group.

A 100% stacked bar chart can help visualize proportional differences.

---

## 7. Practical Implementation Using Python and Pandas

### Step 1: Import Libraries and Create a Dataset

```python
import pandas as pd
import matplotlib.pyplot as plt

data = {
    "Advertising_Spend": [1000, 2000, 3000, 4000, 5000, 6000],
    "Sales": [5000, 8000, 12000, 15000, 19000, 21000],
    "Category": [
        "Electronics", "Clothing", "Electronics",
        "Furniture", "Clothing", "Furniture"
    ],
    "Payment_Method": [
        "UPI", "Card", "UPI", "Card", "UPI", "Card"
    ]
}

df = pd.DataFrame(data)

print(df)
```

### Step 2: Calculate Correlation

```python
correlation = df[
    ["Advertising_Spend", "Sales"]
].corr()

print(correlation)
```

The correlation matrix shows the Pearson correlation between the numerical columns.

### Step 3: Create a Scatter Plot

```python
plt.scatter(
    df["Advertising_Spend"],
    df["Sales"]
)

plt.xlabel("Advertising Spend")
plt.ylabel("Sales Revenue")
plt.title("Advertising Spend vs Sales")
plt.show()
```

This visualization helps examine the direction and pattern of the relationship.

### Step 4: Compare Sales Across Categories

```python
category_summary = df.groupby("Category")["Sales"].agg(
    ["count", "mean", "median", "sum"]
)

print(category_summary)
```

This calculates the number of observations, average sales, median sales, and total sales for each category.

### Step 5: Create a Cross-Tabulation

```python
payment_table = pd.crosstab(
    df["Category"],
    df["Payment_Method"]
)

print(payment_table)
```

### Step 6: Calculate Row Percentages

```python
payment_percentages = pd.crosstab(
    df["Category"],
    df["Payment_Method"],
    normalize="index"
) * 100

print(payment_percentages.round(2))
```

This calculates the percentage distribution of payment methods within each product category.

---

## 8. Business Applications of Bivariate Analysis

Bivariate Analysis is useful in several business scenarios.

| Business Area | Variables | Purpose |
|---|---|---|
| Marketing | Advertising Spend and Sales | Investigate association between spending and revenue |
| E-commerce | Product Category and Sales | Compare category performance |
| Human Resources | Experience and Salary | Examine salary patterns |
| Finance | Discount and Profit | Investigate discount-profit relationships |
| Customer Analytics | Age and Purchase Amount | Study spending patterns |
| Logistics | Shipping Method and Delivery Time | Compare delivery performance |

These analyses support investigation and decision-making, but findings must be interpreted in context.

---

## 9. Common Mistakes to Avoid

1. Assuming correlation proves causation.
2. Ignoring missing values and data quality.
3. Comparing group counts without considering group size.
4. Relying only on the mean without checking the median.
5. Ignoring outliers and unusual observations.
6. Assuming zero Pearson correlation means no relationship of any kind.
7. Reporting charts without explaining their business meaning.
8. Drawing strong conclusions from a very small sample.

---

## 10. Day 15 Practice Tasks

- [ ] Identify numerical and categorical variables in a dataset.
- [ ] Create a scatter plot for two numerical variables.
- [ ] Calculate the correlation coefficient.
- [ ] Compare average and median sales across categories.
- [ ] Create a cross-tabulation using Pandas.
- [ ] Calculate row percentages for categorical data.
- [ ] Write at least three business insights based on the results.
- [ ] Explain why correlation does not prove causation.

---

## 11. Key Takeaways

- Bivariate Analysis investigates two variables together.
- Scatter plots visualize relationships between numerical variables.
- Correlation measures the direction and strength of a linear relationship.
- Grouped statistics compare numerical values across categories.
- Cross-tabulation analyzes combinations of categorical variables.
- Percentages are often more useful than raw counts when group sizes differ.
- Correlation alone cannot establish causation.
- Business insights should be supported by data and interpreted carefully.

