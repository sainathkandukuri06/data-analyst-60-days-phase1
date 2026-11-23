# Day 46 – Advanced Excel Formulas and Data Analysis


### 1. Advanced Excel Formulas
Advanced formulas help perform calculations based on specific conditions.

- `IF()` – Checks a condition and returns a result.
- `SUMIF()` – Adds values based on one condition.
- `SUMIFS()` – Adds values based on multiple conditions.
- `COUNTIF()` – Counts cells matching a condition.
- `COUNTIFS()` – Counts cells matching multiple conditions.
- `AVERAGEIF()` – Calculates the average based on a condition.
- `IFERROR()` – Handles errors in formulas.

**Example:**
```excel
=SUMIF(A2:A5,"Ravi",B2:B5)
```
This formula calculates the total sales made by Ravi.

### 2. Lookup Functions
Lookup functions help retrieve information from tables using matching values.

- `VLOOKUP()` – Searches vertically in a table.
- `HLOOKUP()` – Searches horizontally.
- `XLOOKUP()` – Searches for matching values in different directions.
- `INDEX()` – Returns a value from a specified position.
- `MATCH()` – Finds the position of a matching value.

**Example:**
```excel
=XLOOKUP(E2,A2:A5,B2:B5,"Not Found")
```
This formula searches for the value in E2 and returns the corresponding value from column B.

### 3. Logical Functions
Logical functions help make decisions based on specified conditions.

- `IF()` – Checks whether a condition is TRUE or FALSE.
- `AND()` – Returns TRUE when all conditions are TRUE.
- `OR()` – Returns TRUE when at least one condition is TRUE.
- `NOT()` – Reverses a logical result.

**Example:**
```excel
=IF(B2>=50000,"High Sales","Low Sales")
```

### 4. Conditional Calculations
Conditional calculations help analyze data based on specific business requirements.

**Examples:**

Count sales greater than ₹50,000:
```excel
=COUNTIF(B2:B10,">50000")
```

Calculate average sales for the East region:
```excel
=AVERAGEIF(A2:A10,"East",B2:B10)
```

# Real-World Business Applications

Advanced Excel formulas are useful in business scenarios such as:

- Calculating total sales for each region.
- Identifying high-performing employees.
- Counting completed orders.
- Calculating average employee sales.
- Retrieving employee details from large datasets.
- Comparing business performance using conditions.

# Practical Tasks
1. Practiced SUMIF() and SUMIFS().
2. Practiced COUNTIF() and COUNTIFS().
3. Learned IF(), AND(), and OR().
4. Practiced VLOOKUP() and XLOOKUP().
5. Understood INDEX() and MATCH().
6. Explored conditional calculations.
7. Studied employee sales performance analysis.

# Key Learnings
- Learned how to perform conditional calculations.
- Understood how lookup functions retrieve information.
- Practiced logical functions for decision-making.
- Learned how to analyze business datasets.
- Understood how Excel formulas reduce manual work.
- Improved my data analysis and problem-solving skills.

