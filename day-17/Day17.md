# Day 17: Confidence Intervals, Hypothesis Testing & Statistical Decision-Making

# Learning Objectives

- Understand confidence intervals and their importance.
- Learn the difference between population and sample statistics.
- Calculate confidence intervals using statistical formulas.
- Understand null and alternative hypotheses.
- Interpret p-values and significance levels.
- Identify Type I and Type II errors.
- Understand statistical power.
- Apply hypothesis testing to A/B testing.
- Distinguish statistical significance from business significance.
- Communicate statistical findings through business reports.

# 1. Confidence Intervals

#  What Is a Confidence Interval?

A confidence interval (CI) is a range of plausible values used to estimate an unknown population parameter from sample data.

For example, an e-commerce company wants to estimate the average amount customers spend per order. Instead of analyzing every order, the analyst selects a sample and calculates the average.

The sample average provides a point estimate, while the confidence interval communicates the uncertainty associated with that estimate.

### Population vs. Sample

| Term | Description |
|---|---|
| Population | The complete group being studied |
| Sample | A subset selected from the population |
| Population Mean | The actual average of the population |
| Sample Mean | The average calculated from the sample |
| Standard Error | Measures the sampling uncertainty of an estimator |
| Margin of Error | The amount added to and subtracted from the estimate |

### Confidence Interval Formula for a Mean

When the population standard deviation is known and the normal approximation is appropriate:

**Confidence Interval = Sample Mean ± (Critical z-value × Standard Error)**

\[
CI=\bar{x}\pm z^*\frac{\sigma}{\sqrt{n}}
\]

Where:

- \(\bar{x}\) = Sample mean
- \(z^*\) = Critical z-value
- \(\sigma\) = Population standard deviation
- \(n\) = Sample size
- \(\frac{\sigma}{\sqrt{n}}\) = Standard error

When the population standard deviation is unknown, a t-critical value and sample standard deviation are commonly used:

\[
CI=\bar{x}\pm t^*\frac{s}{\sqrt{n}}
\]

### Example

Suppose an online store has the following sample statistics:

- Sample mean = ₹1,200
- Population standard deviation = ₹900
- Sample size = 500
- Confidence level = 95%
- Critical z-value = 1.96

Step 1: Calculate the standard error.

\[
SE=\frac{900}{\sqrt{500}}\approx40.25
\]

Step 2: Calculate the margin of error.

\[
ME=1.96\times40.25\approx78.89
\]

Step 3: Calculate the confidence interval.

\[
CI=1200\pm78.89
\]

**Final Result: ₹1,121.11 to ₹1,278.89**

Under the assumptions of this method, the interval estimates a plausible range for the population's average order value.

### Important Points

- A confidence interval quantifies estimation uncertainty.
- Larger samples generally produce narrower confidence intervals.
- Greater variability generally produces wider confidence intervals.
- A biased sample can produce misleading estimates even when the sample is large.
- A 95% confidence level describes the long-run coverage of the interval-building method.

---

## 2. Hypothesis Testing

### What Is Hypothesis Testing?

Hypothesis testing is a statistical method used to evaluate a claim about a population using sample data.

It helps analysts determine whether the observed results provide sufficient evidence against a specified assumption.

### Null Hypothesis (H₀)

The null hypothesis generally represents no difference, no effect, or no relationship.

Example:

The old and new checkout pages have the same conversion rate.

\[
H_0:p_{\text{new}}=p_{\text{old}}
\]

### Alternative Hypothesis (H₁)

The alternative hypothesis represents a competing claim.

Example:

The old and new checkout pages have different conversion rates.

\[
H_1:p_{\text{new}}\ne p_{\text{old}}
\]

The alternative hypothesis can also be directional when the business question specifically concerns an increase or decrease.

### Steps in Hypothesis Testing

1. Define the business question.
2. Formulate the null and alternative hypotheses.
3. Select a significance level.
4. Choose an appropriate statistical test.
5. Calculate the test statistic.
6. Determine the p-value.
7. Compare the p-value with the significance level.
8. Interpret the result in business terms.

### Significance Level

The significance level is represented by alpha (\(\alpha\)).

A commonly used significance level is:

\[
\alpha=0.05
\]

It controls the long-run Type I error rate when the test assumptions hold.

### Decision Rule

- If p-value ≤ α, reject the null hypothesis.
- If p-value > α, fail to reject the null hypothesis.

Failing to reject the null hypothesis does not prove that the null hypothesis is true.

---

## 3. P-Values

### What Is a P-Value?

A p-value measures how extreme the observed test result, or a more extreme result, would be under the null hypothesis and the specified statistical model.

A small p-value indicates that the observed result is relatively inconsistent with the null hypothesis.

### Interpretation

| P-value | Interpretation at α = 0.05 |
|---|---|
| 0.001 | Statistically significant |
| 0.020 | Statistically significant |
| 0.049 | Statistically significant |
| 0.050 | At the significance threshold |
| 0.113 | Not statistically significant |
| 0.400 | Not statistically significant |

**Important:** A p-value is not the probability that the null hypothesis is true.

### Statistical Significance vs. Business Significance

Statistical significance indicates whether the evidence meets a statistical decision threshold.

Business significance evaluates whether the size of the observed effect is meaningful enough to justify a decision.

A result can be statistically significant but have little practical value. A potentially valuable result can also remain statistically uncertain.

---

## 4. Type I and Type II Errors

Statistical decisions can be incorrect because sample data contain uncertainty.

### Type I Error

A Type I error occurs when a true null hypothesis is rejected.

It is also known as a false positive.

Example: An analyst concludes that a redesigned checkout page improves conversion when it actually has no effect.

The significance level controls the Type I error probability under the null hypothesis and the assumptions of the test.

### Type II Error

A Type II error occurs when an analyst fails to reject a false null hypothesis.

It is also known as a false negative.

Example: A checkout redesign genuinely improves conversion, but the experiment fails to detect the improvement.

### Comparison

| Feature | Type I Error | Type II Error |
|---|---|---|
| Meaning | False positive | False negative |
| Statistical symbol | α | β |
| Incorrect decision | Reject a true null hypothesis | Fail to reject a false null hypothesis |
| Business consequence | Acting on a nonexistent effect | Missing a real effect |

### Statistical Power

Statistical power is the probability of correctly rejecting the null hypothesis when a specified alternative is true.

\[
\text{Power}=1-\beta
\]

If the Type II error probability is 0.20:

\[
\text{Power}=1-0.20=0.80
\]

Therefore, statistical power is 80%.

Power can often be improved by increasing sample size, reducing measurement noise, and using an appropriate experimental design.

---

## 5. A/B Testing

### What Is A/B Testing?

A/B testing is a controlled experiment used to compare two versions of a product, webpage, advertisement, or other business experience.

It helps determine whether a change affects a predefined metric.

### Example: E-Commerce Conversion

An online store tests a redesigned checkout page.

| Metric | Control Group | Treatment Group |
|---|---:|---:|
| Visitors | 10,000 | 10,000 |
| Purchases | 500 | 550 |
| Conversion Rate | 5.0% | 5.5% |

### Conversion Rate Formula

\[
\text{Conversion Rate}=
\frac{\text{Number of Conversions}}{\text{Total Eligible Visitors}}\times100
\]

Control conversion rate:

\[
\frac{500}{10000}\times100=5\%
\]

Treatment conversion rate:

\[
\frac{550}{10000}\times100=5.5\%
\]

### Absolute Lift

\[
\text{Absolute Lift}=5.5\%-5.0\%
\]

**Absolute lift = 0.5 percentage points.**

### Relative Lift

\[
\text{Relative Lift}=
\frac{5.5\%-5.0\%}{5.0\%}\times100
\]

**Relative lift = 10%.**

Absolute lift and relative lift communicate different aspects of an experiment's result.

### Two-Proportion Z-Test

For two independent conversion proportions, a two-proportion z-test can be used when its assumptions are appropriate.

The pooled proportion under the null hypothesis is:

\[
\hat p=\frac{x_1+x_2}{n_1+n_2}
\]

The standard error under the null hypothesis is:

\[
SE_0=\sqrt{\hat p(1-\hat p)
\left(\frac{1}{n_1}+\frac{1}{n_2}\right)}
\]

The test statistic is:

\[
z=\frac{p_2-p_1}{SE_0}
\]

For the example above:

- Pooled proportion = 0.0525
- Standard error under the null ≈ 0.003154
- Z-statistic ≈ 1.585
- Two-sided p-value ≈ 0.113

Since the p-value is greater than 0.05, we fail to reject the null hypothesis at the 5% significance level.

The observed increase does not provide sufficient statistical evidence of a difference under this test. It does not prove that both pages perform identically.

### Important A/B Testing Considerations

- Randomly assign eligible users to groups.
- Use the same conversion definition for both groups.
- Select the primary metric before the experiment.
- Choose an appropriate sample size and experiment duration.
- Avoid changing the analysis plan just to obtain a significant result.
- Examine confidence intervals and practical business impact.
- Check guardrail metrics such as refunds, cancellations, and customer complaints.

---

## 6. Business Reporting

A Data Analyst must translate statistical calculations into understandable business recommendations.

### Example Business Report

**Objective:** Evaluate whether a redesigned checkout page changes purchase conversion.

**Control:** 5.0% conversion from 10,000 visitors.

**Treatment:** 5.5% conversion from 10,000 visitors.

**Observed Improvement:** 0.5 percentage points in absolute terms and 10% in relative terms.

**Statistical Result:** The two-sided z-test produced a z-statistic of approximately 1.585 and a p-value of approximately 0.113.

**Conclusion:** The difference was not statistically significant at the 5% level.

**Recommendation