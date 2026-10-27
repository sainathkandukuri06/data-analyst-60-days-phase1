# Day 19: Correlation Analysis and Relationships Between Variables

## 1. Introduction

Correlation Analysis is an important statistical technique used by Data Analysts to understand the relationship between two variables.

In real-world business situations, analysts often need to answer questions such as:

- Does advertising expenditure affect sales?
- Is there a relationship between product price and demand?
- Do students who study more hours achieve higher marks?
- Is customer satisfaction related to customer retention?
- Does a discount increase the number of products sold?

Correlation analysis helps us identify whether two variables move together and how strong their relationship is.

**Day 19 Objective:** Understand correlation, its types, correlation coefficients, formulas, interpretation, practical examples, and its applications in real-world data analysis.

---

## 2. What Is Correlation?

Correlation is a statistical measure that describes the strength and direction of the relationship between two variables.

A variable is any characteristic that can take different values.

Examples:

- Sales revenue
- Advertising expenditure
- Product price
- Customer age
- Study hours
- Examination marks

### Example

Consider the following advertising and sales data:

| Advertising Spend (₹) | Sales Revenue (₹) |
|---:|---:|
| 1,000 | 5,000 |
| 2,000 | 8,000 |
| 3,000 | 11,000 |
| 4,000 | 14,000 |
| 5,000 | 17,000 |

As advertising expenditure increases, sales revenue also increases.

This dataset shows a perfect positive linear relationship.

**Important:** Correlation helps us identify relationships, but it does not automatically prove that one variable causes changes in another.

---

## 3. Types of Correlation

There are three major types of correlation based on direction.

### 3.1 Positive Correlation

Positive correlation occurs when two variables tend to increase or decrease together.

**Example:**

- Advertising expenditure increases.
- Sales revenue tends to increase.

Other examples:

- Study hours and examination marks
- Customer visits and total purchases
- Experience and salary, in some job markets

The correlation coefficient is greater than zero.

\[
0 < r \leq 1
\]

### 3.2 Negative Correlation

Negative correlation occurs when one variable tends to increase while the other decreases.

**Example:**

- Product price increases.
- Quantity demanded may decrease.

Other examples:

- Vehicle speed and travel time over a fixed distance
- Product discounts and selling prices
- Customer waiting time and customer satisfaction, in some situations

The correlation coefficient is less than zero.

\[
-1 \leq r < 0
\]

### 3.3 Zero or No Linear Correlation

This occurs when there is no meaningful linear relationship between two variables.

**Example:**

A person's shoe size and their monthly electricity bill would generally have no meaningful linear relationship.

The correlation coefficient is approximately:

\[
r = 0
\]

**Important:** A zero correlation does not necessarily mean that no relationship exists. The variables could have a nonlinear relationship that Pearson correlation does not capture.

---

## 4. Understanding the Correlation Coefficient

The correlation coefficient is a numerical value used to measure the direction and strength of a relationship.

For Pearson correlation, the coefficient is represented by `r`.

Its value ranges from -1 to +1.

| Correlation Coefficient | Interpretation |
|---:|---|
| +1.00 | Perfect positive linear correlation |
| +0.80 | Strong positive linear correlation |
| +0.50 | Moderate positive linear correlation |
| +0.20 | Weak positive linear correlation |
| 0.00 | No linear correlation |
| -0.20 | Weak negative linear correlation |
| -0.50 | Moderate negative linear correlation |
| -0.80 | Strong negative linear correlation |
| -1.00 | Perfect negative linear correlation |

These strength labels are general guidelines, not universal statistical rules. The appropriate interpretation depends on the dataset and business context.

### How to interpret correlation

- The **sign** tells us the direction of the relationship.
- The **absolute value** tells us the strength of the linear relationship.
- A value close to +1 indicates a strong positive linear relationship.
- A value close to -1 indicates a strong negative linear relationship.
- A value close to 0 indicates a weak linear relationship.

---

## 5. Pearson Correlation Coefficient

Pearson correlation is commonly used to measure the strength and direction of a linear relationship between two numerical variables.

### Formula

\[
r =
\frac{\sum (x_i-\bar{x})(y_i-\bar{y})}
{\sqrt{\sum(x_i-\bar{x})^2
\sum(y_i-\bar{y})^2}}
\]

Where:

- \(x_i\) = individual value of variable X
- \(y_i\) = individual value of variable Y
- \(\bar{x}\) = mean of variable X
- \(\bar{y}\) = mean of variable Y
- \(\sum\) = summation of all observations
- \(r\) = Pearson correlation coefficient

### What happens behind the formula?

1. Calculate the mean of both variables.
2. Calculate how far each observation is from its variable's mean.
3. Multiply the deviations of X and Y for each observation.
4. Add the products of the deviations.
5. Divide by the product of the variables' deviation magnitudes.

The result measures how consistently the two variables vary together relative to their individual variability.

### Why do we use Pearson correlation?

It is useful when:

- Both variables are numerical.
- We want to measure a linear relationship.
- The data contains meaningful paired observations.

Pearson correlation can be sensitive to outliers. For formal statistical inference, assumptions such as independent observations and suitable distributional conditions also matter.

---

## 6. Spearman Rank Correlation

Spearman correlation measures the strength and direction of a monotonic relationship using the ranks of observations.

A monotonic relationship means that as one variable increases, the other generally moves in one direction, although the relationship does not have to be a straight line.

It is useful when:

- Data is ordinal or rank-based.
- The relationship is monotonic but not necessarily linear.
- Outliers make Pearson correlation less suitable.
- We want to compare rankings.

### Example

Suppose customers rank three products:

| Product | Price Rank | Preference Rank |
|---|---:|---:|
| A | 1 | 3 |
| B | 2 | 2 |
| C | 3 | 1 |

The rankings move in opposite directions, indicating a negative rank relationship.

For data without tied ranks, Spearman's coefficient can be calculated using:

\[
\rho = 1-\frac{6\sum d_i^2}{n(n^2-1)}
\]

Where:

- \(d_i\) = difference between the two ranks for observation i
- \(n\) = number of observations
- \(\rho\) = Spearman rank correlation coefficient

When ranks contain ties, software generally calculates the correlation between the assigned ranks rather than relying directly on the simplified formula.

---

## 7. Correlation vs. Causation

This is one of the most important concepts for a Data Analyst.

**Correlation does not imply causation.**

Correlation indicates that variables are associated. Causation means that changing one variable produces a change in another, under a clearly defined causal interpretation.

### Business example

Suppose an analyst observes:

- Ice cream sales increase during summer.
- Swimming-related accidents also increase during summer.

These variables may be positively correlated.

However, buying ice cream does not necessarily cause swimming accidents. A third variable—hot weather or increased outdoor activity—may influence both.

This is called a **confounding variable**.

### Why does this matter?

If a company assumes correlation proves causation, it may make incorrect business decisions.

To investigate causation, analysts may need:

- Controlled experiments
- A/B testing
- Randomized trials
- Natural experiments
- Causal inference methods
- Additional domain knowledge

---

## 8. Correlation Matrix

A correlation matrix is a table that displays the pairwise correlation coefficients among multiple numerical variables.

### Example

Consider a sales dataset with these variables:

- Advertising Spend
- Sales Revenue
- Discount Percentage
- Customer Satisfaction

| Variable | Advertising | Sales | Discount | Satisfaction |
|---|---:|---:|---:|---:|
| Advertising | 1.00 | 0.90 | 0.10 | 0.30 |
| Sales | 0.90 | 1.00 | 0.20 | 0.40 |
| Discount | 0.10 | 0.20 | 1.00 | 0.25 |
| Satisfaction | 0.30 | 0.40 | 0.25 | 1.00 |

*The values are illustrative and are not based on an actual business dataset.*

### How to read the matrix

- Advertising and sales have a strong positive correlation of 0.90.
- Discount and sales have a weak positive correlation of 0.20.
- Sales and customer satisfaction have a moderate positive correlation of 0.40, depending on the context.
- Each variable has a correlation of 1.00 with itself.

A correlation matrix helps analysts quickly identify relationships worth investigating further.

---

## 9. Correlation Heatmap

A correlation heatmap is a visualization of a correlation matrix.

Different colors represent different correlation values.

Typical interpretation:

- Values near +1 indicate strong positive correlation.
- Values near -1 indicate strong negative correlation.
- Values near 0 indicate weak linear correlation.

### Why use a heatmap?

A heatmap makes it easier to:

- Compare many variable relationships.
- Identify highly correlated features.
- Discover potential multicollinearity.
- Find relationships worth investigating.
- Communicate statistical findings to stakeholders.

A heatmap should be supported by numerical values and business context. Color alone does not explain whether a relationship is meaningful.

---

## 10. Practical Implementation Using Python

Python libraries such as Pandas, NumPy, Matplotlib, and Seaborn help analysts calculate and visualize correlation.

### Step 1: Import the libraries

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

### Step 2: Create a sample dataset

```python
data = {
    "Advertising_Spend": [1000, 2000, 3000, 4000, 5000],
    "Sales_Revenue": [5000, 8000, 11000, 14000, 17000],
    "Discount_Percentage": [5, 10, 15, 20, 25]
}

df = pd.DataFrame(data)

print(df)
```

### Step 3: Calculate Pearson correlation

```python
correlation = df.corr(method="pearson")

print(correlation)
```

The `corr()` method calculates correlations between the numerical columns.

### Step 4: Calculate Spearman correlation

```python
spearman_corr = df.corr(method="spearman")

print(spearman_corr)
```

Spearman correlation calculates relationships based on the ranks of observations.

### Step 5: Create a correlation heatmap

```python
plt.figure(figsize=(8, 5))

sns.heatmap(
    correlation,
    annot=True,
    cmap="coolwarm",
    vmin=-1,
    vmax=1
)

plt.title("Correlation Heatmap")
plt.show()
```

### Understanding the code

- `plt.figure()` sets the figure size.
- `sns.heatmap()` displays the correlation matrix as a heatmap.
- `annot=True` displays the correlation values.
- `cmap="coolwarm"` selects a diverging color palette.
- `vmin=-1` and `vmax=1` set the color scale.
- `plt.show()` displays the visualization.

In this sample dataset, advertising expenditure and sales revenue have a perfect positive linear correlation because sales increase by a constant amount for every increase in advertising expenditure.

This is a deliberately simple example. Real-world datasets rarely follow such a perfect pattern.

---

## 11. Practical Implementation Using Excel

Excel provides built-in functions to calculate correlation.

### CORREL function

Syntax:

```excel
=CORREL(array1, array2)
```

Example:

```excel
=CORREL(A2:A6,B2:B6)
```

Assume:

- Column A contains advertising expenditure.
- Column B contains sales revenue.
- Rows 2 through 6 contain five observations.

Excel returns the Pearson correlation coefficient.

### Using Excel's Data Analysis ToolPak

1. Open Excel.
2. Select **Data**.
3. Open **Data Analysis**.
4. Select **Correlation**.
5. Choose the input range.
6. Specify whether the data is grouped by columns or rows.
7. Select the output range.
8. Click **OK**.

If Data Analysis is unavailable, enable the Analysis ToolPak through Excel's Add-ins settings.

---

## 12. Correlation in Power BI

Power BI can help analysts explore relationships through scatter charts, calculated measures, and Python-based analysis.

### Scatter chart approach

1. Load a dataset into Power BI.
2. Add a scatter chart.
3. Place one numerical measure on the X-axis.
4. Place another numerical measure on the Y-axis.
5. Add a category to the Details field, when available, to show individual observations.
6. Review the distribution of points.

### Example

- X-axis: Advertising Spend
- Y-axis: Sales Revenue
- Details: Product or Campaign

If the points generally move upward from left to right, the chart suggests a positive relationship.

If they move downward, it suggests a negative relationship.

If they form a curved pattern, the relationship may be nonlinear.

**Important:** A scatter chart visually suggests relationships; it does not automatically provide a Pearson correlation coefficient. You can calculate the coefficient in Python, Excel, or another supported analysis workflow and bring the result into your report.

---

## 13. Common Mistakes in Correlation Analysis

### Mistake 1: Assuming correlation proves causation

Two variables may move together because of a third variable.

**Solution:** Investigate possible confounding variables and use suitable causal methods when necessary.

### Mistake 2: Ignoring outliers

A few unusual observations can significantly change Pearson correlation.

**Solution:** Inspect scatter plots, validate unusual values, and compare results with and without influential observations when appropriate.

### Mistake 3: Assuming zero correlation means no relationship

Pearson correlation measures linear relationships.

**Solution:** Use scatter plots and investigate possible nonlinear relationships.

### Mistake 4: Using correlation without understanding the variables

A numerical relationship may not be useful or meaningful for the business problem.

**Solution:** Combine statistical results with business context.

### Mistake 5: Ignoring missing values

Missing observations can change which rows are used to calculate correlation.

**Solution:** Check missingness and understand how the analysis handles incomplete data.

### Mistake 6: Confusing correlation with prediction

A strong correlation alone does not establish a reliable predictive model.

**Solution:** Evaluate predictive performance using appropriate validation methods.

---

## 14. Real-World Applications of Correlation

### Sales Analytics

Analyze relationships between advertising expenditure, sales revenue, product price, and discounts.

### Marketing Analytics

Explore relationships between campaign engagement, website visits, conversions, and customer retention.

### Financial Analytics

Investigate how asset returns move together and assess diversification opportunities.

### Customer Analytics

Study associations among satisfaction scores, purchase frequency, spending, and churn.

### Human Resources Analytics

Explore relationships between training hours, employee performance, experience, and compensation.

### Education Analytics

Analyze associations between attendance, study time, practice tests, and examination results.

In every case, correlation is a starting point for investigation rather than proof of cause and effect.

---

## 15. Day 19 Practice Exercises

Complete the following exercises to strengthen your understanding.

### Beginner Level

1. Define correlation in your own words.
2. Explain positive, negative, and zero linear correlation.
3. What is the range of Pearson's correlation coefficient?
4. What does a correlation coefficient of -0.85 suggest?
5. Explain the difference between correlation and causation.

### Intermediate Level

6. Calculate the correlation between advertising expenditure and sales in Excel.
7. Create a correlation matrix using Pandas.
8. Draw a heatmap using Seaborn.
9. Explain why outliers can affect Pearson correlation.
10. Compare Pearson and Spearman correlation.

### Advanced Level

11. Identify highly correlated variables in a business dataset.
12. Investigate whether a strong relationship remains after examining outliers.
13. Find an example of a possible confounding variable.
14. Explain why correlation may not be sufficient to establish causation.
15. Write three business recommendations supported by correlation analysis, clearly distinguishing evidence of association from evidence of causation.

---

