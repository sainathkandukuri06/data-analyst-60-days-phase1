# Day 42 – Excel Logical and Conditional Functions

Excel provides several functions that help Data Analysts make decisions, evaluate conditions, calculate values based on criteria, and handle errors.

These functions are useful when analyzing employee records, sales reports, customer information, and business performance data.

## 1. IF Function

The IF function checks a condition and returns one result if the condition is TRUE and another result if it is FALSE.

### Syntax

```excel
=IF(condition, value_if_true, value_if_false)
```

### Example

Suppose we have student marks and want to identify whether students passed or failed.

| Student | Marks | Result |
|---|---:|---|
| Ravi | 85 | Pass |
| Kumar | 35 | Fail |
| Suresh | 65 | Pass |

Formula:

```excel
=IF(B2>=40,"Pass","Fail")
```

**Explanation:**
- If marks are greater than or equal to 40, the result is Pass.
- If marks are below 40, the result is Fail.

**Real-world application:** Evaluating employee performance, student results, and sales targets.

---

## 2. AND Function

The AND function checks multiple conditions and returns TRUE only when all conditions are satisfied.

### Syntax

```excel
=AND(condition1, condition2, ...)
```

### Example

An employee qualifies for a bonus when:
- Sales are greater than ₹50,000.
- Attendance is greater than 90%.

Formula:

```excel
=AND(B2>50000,C2>90)
```

**Explanation:**

Both conditions must be TRUE to receive a TRUE result. If even one condition is FALSE, the result will be FALSE.

**Real-world application:** Checking employee bonus eligibility and evaluating business requirements.

---

## 3. OR Function

The OR function checks multiple conditions and returns TRUE if at least one condition is TRUE.

### Syntax

```excel
=OR(condition1, condition2, ...)
```

### Example

An employee qualifies for recognition if:
- Sales are greater than ₹50,000.
- Customer rating is greater than 4.

Formula:

```excel
=OR(B2>50000,C2>4)
```

**Explanation:**

Only one condition needs to be TRUE for the OR function to return TRUE.

**Real-world application:** Identifying eligible customers, employees, and products based on multiple conditions.

---

## 4. SUMIF Function

The SUMIF function adds values that satisfy a particular condition.

### Syntax

```excel
=SUMIF(range, criteria, sum_range)
```

### Example

Suppose we have product sales data.

| Product | Sales |
|---|---:|
| Laptop | 50000 |
| Mobile | 30000 |
| Laptop | 40000 |

To calculate total Laptop sales:

```excel
=SUMIF(A2:A4,"Laptop",B2:B4)
```

**Result:** 90000

**Explanation:**
- A2:A4 is the range where Excel checks the product names.
- "Laptop" is the condition.
- B2:B4 contains the values to add.

**Real-world application:** Calculating total sales by product, department, category, or region.

---

## 5. COUNTIF Function

The COUNTIF function counts the number of cells that satisfy a specific condition.

### Syntax

```excel
=COUNTIF(range, criteria)
```

### Example

Suppose we have employee department information and want to count employees in the IT department.

Formula:

```excel
=COUNTIF(A2:A20,"IT")
```

**Explanation:**

Excel counts how many cells in the selected range contain the value IT.

**Real-world application:** Counting employees by department, completed orders, and customers by category.

---

## 6. AVERAGEIF Function

The AVERAGEIF function calculates the average of values that satisfy a particular condition.

### Syntax

```excel
=AVERAGEIF(range, criteria, average_range)
```

### Example

Suppose we want to calculate the average sales of Laptop products.

Formula:

```excel
=AVERAGEIF(A2:A10,"Laptop",B2:B10)
```

**Explanation:**
- A2:A10 contains product names.
- Laptop is the condition.
- B2:B10 contains sales values.

Excel calculates the average using only the sales values belonging to Laptop products.

**Real-world application:** Calculating average sales by product, department, region, or employee category.

---

## 7. IFERROR Function

The IFERROR function helps handle errors in Excel formulas.

When a formula produces an error, IFERROR displays an alternative value instead of the error message.

### Syntax

```excel
=IFERROR(value, value_if_error)
```

### Example

```excel
=IFERROR(A2/B2,"Invalid Calculation")
```

**Explanation:**

- If the division works correctly, Excel displays the calculated result.
- If the formula produces an error, Excel displays "Invalid Calculation".

For example, dividing a number by zero normally produces a `#DIV/0!` error. IFERROR can handle this situation.

**Real-world application:** Maintaining clean reports and preventing formula errors from appearing in dashboards.

---

## 8. Summary of Functions

| Function | Purpose |
|---|---|
| IF | Checks a condition and returns different results. |
| AND | Returns TRUE when all conditions are TRUE. |
| OR | Returns TRUE when at least one condition is TRUE. |
| SUMIF | Adds values based on a condition. |
| COUNTIF | Counts cells based on a condition. |
| AVERAGEIF | Calculates an average based on a condition. |
| IFERROR | Handles errors in formulas. |

