# Day 18: Statistics for Data Analysts — Percentiles, Quartiles, IQR, Distribution, Correlation & Covariance

#  Learning Objectives

- Understand percentiles and their applications.
- Learn quartiles and how they divide a dataset.
- Calculate the Interquartile Range (IQR).
- Identify potential outliers using the IQR method.
- Understand different types of data distributions.
- Learn correlation and its interpretation.
- Understand covariance and how it differs from correlation.
- Apply statistical concepts using Microsoft Excel.
- Interpret statistical results in a business context.

## 1. Percentiles

### Definition

A percentile indicates the position of a value relative to the other observations in a dataset.

For example, the 90th percentile is a value at or below which approximately 90% of observations fall, depending on the percentile calculation convention.

### Important Percentiles

- P25: 25th percentile
- P50: 50th percentile, or median
- P75: 75th percentile
- P90: 90th percentile
- P95: 95th percentile

### Excel Formula

```excel
=PERCENTILE.INC(A2:A101,0.90)
```

This calculates the 90th percentile of the values in the specified range.

### Business Applications

- Comparing employee salaries.
- Understanding customer spending.
- Analyzing delivery times.
- Measuring website response times.
- Identifying high-value customers.

---

## 2. Quartiles

### Definition

Quartiles divide an ordered dataset into four sections, each containing approximately 25% of the observations.

| Quartile | Meaning |
|---|---|
| Q1 | First quartile; 25th percentile |
| Q2 | Second quartile; 50th percentile or median |
| Q3 | Third quartile; 75th percentile |

### Excel Formulas

```excel
=QUARTILE.INC(A2:A101,1)
```

Calculates Q1.

```excel
=QUARTILE.INC(A2:A101,2)
```

Calculates Q2.

```excel
=QUARTILE.INC(A2:A101,3)
```

Calculates Q3.

### Business Applications

Quartiles help analysts segment customers, compare salary distributions, evaluate sales performance, and understand the spread of business metrics.

---

## 3. Interquartile Range (IQR)

### Definition

The Interquartile Range measures the spread of the middle 50% of observations in a dataset.

### Formula

**IQR = Q3 − Q1**

### Example

Suppose:

- Q1 = 20
- Q3 = 60

Then:

IQR = 60 − 20 = 40

The IQR is 40.

### Outlier Detection Using IQR

The IQR method identifies potential outliers using lower and upper fences.

**Lower Fence = Q1 − 1.5 × IQR**

**Upper Fence = Q3 + 1.5 × IQR**

Values outside these fences are flagged as potential outliers.

### Excel Formula

```excel
=QUARTILE.INC(A2:A101,3)-QUARTILE.INC(A2:A101,1)
```

### Why IQR Is Important

- Helps identify unusual transactions.
- Measures the spread of central observations.
- Is less affected by extreme values than the range.
- Supports data quality investigations.
- Helps summarize skewed business data.

**Note:** A potential outlier should be investigated before it is removed. It may represent a genuine business event rather than an error.

---

## 4. Understanding Data Distributions

### Definition

A data distribution describes how observations are spread across different values.

Understanding distributions helps analysts identify patterns, unusual values, and variability.

### Types of Distributions

#### A. Symmetric Distribution

A symmetric distribution has approximately similar shapes on both sides of its center.

For a perfectly symmetric, unimodal normal distribution:

Mean = Median = Mode

#### B. Right-Skewed Distribution

A right-skewed distribution has a long tail toward higher values.

The mean is often greater than the median.

**Example:** Customer spending where a small number of customers spend significantly more than the majority.

#### C. Left-Skewed Distribution

A left-skewed distribution has a long tail toward lower values.

The mean is often less than the median.

**Example:** Examination scores where most students score highly but a few receive very low marks.

#### D. Uniform Distribution

A uniform distribution has approximately equal probability density across a defined interval.

### Tools for Understanding Distributions

- Histograms
- Mean and median
- Minimum and maximum values
- Quartiles
- IQR
- Box plots

These tools help analysts understand the shape and spread of a dataset.

---

## 5. Correlation

### Definition

Correlation measures the direction and strength of a linear relationship between two variables.

It helps analysts determine whether two variables tend to move together.

### Pearson Correlation Coefficient

The Pearson correlation coefficient is represented by **r**.

Its value ranges from -1 to +1.

| Correlation Value | Interpretation |
|---|---|
| +1 | Perfect positive linear relationship |
| Close to +1 | Strong positive linear relationship |
| Close to 0 | Weak or no linear relationship |
| Close to -1 | Strong negative linear relationship |
| -1 | Perfect negative linear relationship |

The strength categories are general guidelines and depend on the context.

### Types of Correlation

**Positive Correlation:** Both variables tend to increase together.

Example: Advertising expenditure and sales revenue.

**Negative Correlation:** One variable tends to increase as the other decreases.

Example: Product price and quantity demanded may move in opposite directions.

**Zero Linear Correlation:** There is no linear relationship between the variables. A nonlinear relationship may still exist.

### Excel Formula

```excel
=CORREL(B2:B101,C2:C101)
```

This calculates Pearson's correlation coefficient for two corresponding data ranges.

### Business Applications

- Analyzing advertising expenditure and sales.
- Studying website visits and purchases.
- Investigating study hours and examination scores.
- Comparing product prices and demand.
- Understanding relationships between business KPIs.

### Important Principle

**Correlation does not imply causation.**

A correlation between two variables does not prove that one variable causes changes in the other. Other variables may influence both.

---

## 6. Covariance

### Definition

Covariance measures whether two variables tend to move together or in opposite directions.

### Types of Covariance

| Covariance | Interpretation |
|---|---|
| Positive | Variables tend to move in the same direction |
| Negative | Variables tend to move in opposite directions |
| Zero | No linear co-movement as measured by covariance |

### Sample Covariance Formula

**Sample covariance = Sum of products of deviations / (n − 1)**

Mathematically:

sXY = Σ[(Xi − X̄)(Yi − Ȳ)] / (n − 1)

Where:

- Xi = Individual observation of variable X
- Yi = Individual observation of variable Y
- X̄ = Mean of variable X
- Ȳ = Mean of variable Y
- n = Number of paired observations

### Excel Formulas

For sample covariance:

```excel
=COVARIANCE.S(B2:B101,C2:C101)
```

For population covariance:

```excel
=COVARIANCE.P(B2:B101,C2:C101)
```

### Business Applications

- Understanding how advertising and sales move together.
- Analyzing relationships between business metrics.
- Studying joint variation between financial variables.
- Supporting statistical analysis and modeling.


## 7. Correlation vs. Covariance

| Feature | Correlation | Covariance |
|---|---|---|
| Purpose | Measures direction and standardized strength of a linear relationship | Measures directional co-movement |
| Range | -1 to +1 | No fixed range |
| Units | Unitless | Depends on the units of both variables |
| Interpretation | Easier to compare across variable pairs | Magnitude depends on scale |
| Excel Function | `CORREL()` | `COVARIANCE.S()` |
| Main Use | Relationship analysis | Joint variation analysis |

Correlation is generally easier to interpret because it uses a standardized scale.

## 8. Practical Business Example

Imagine an e-commerce company wants to understand customer spending and the relationship between advertising expenditure and sales revenue.

A Data Analyst can:

1. Calculate customer spending percentiles.
2. Determine Q1, Q2, and Q3.
3. Calculate the IQR.
4. Identify potential outliers using the IQR fences.
5. Create a histogram to understand the spending distribution.
6. Calculate the correlation between advertising and sales.
7. Calculate covariance to examine directional co-movement.
8. Write business observations based on the results.

### Expected Business Insights

- Understand typical customer spending.
- Identify unusually high or low transactions.
- Determine whether customer spending is skewed.
- Evaluate whether advertising and sales are linearly associated.
- Communicate findings without confusing correlation with causation.

## 9. Key Excel Functions Learned

| Function | Purpose |
|---|---|
| `PERCENTILE.INC()` | Calculates a specified percentile |
| `QUARTILE.INC()` | Calculates a quartile |
| `MEDIAN()` | Calculates the median |
| `CORREL()` | Calculates Pearson correlation |
| `COVARIANCE.S()` | Calculates sample covariance |
| `COVARIANCE.P()` | Calculates population covariance |
| `MIN()` | Returns the minimum value |
| `MAX()` | Returns the maximum value |

## 10. Practice Tasks

- [ ] Calculate the 25th, 50th, 75th, and 90th percentiles of customer spending.
- [ ] Calculate Q1, Q2, and Q3.
- [ ] Calculate the IQR.
- [ ] Calculate the lower and upper outlier fences.
- [ ] Create a histogram of customer spending.
- [ ] Identify and investigate potential outliers.
- [ ] Calculate the correlation between advertising and sales.
- [ ] Calculate sample covariance for advertising and sales.
- [ ] Write three business observations based on the results.

---

## 11. Key Takeaways

- Percentiles describe the relative position of observations.
- Quartiles divide ordered data into four sections.
- IQR measures the spread of the middle 50% of observations.
- Outlier fences help identify unusual values for investigation.
- Distributions reveal the shape and spread of data.
- Correlation measures the direction and strength of a linear relationship.
- Covariance measures directional co-movement.
- Correlation does not establish causation.
- Excel makes statistical analysis easier to perform and repeat.

---

# Tools Used

- Microsoft Excel
- Statistical Analysis
- Exploratory Data Analysis (EDA)