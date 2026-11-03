# Day 26 - SQL Date Functions and String Functions


# Learning Objectives

- Understand SQL Date Functions.
- Extract year, month, and day from dates.
- Calculate differences between dates.
- Add or subtract days from dates.
- Understand SQL String Functions.
- Convert text into uppercase and lowercase.
- Combine multiple strings.
- Extract specific characters from strings.
- Clean inconsistent text data.

# 1. SQL Date Functions

Date Functions are built-in SQL functions used to manipulate and analyze date and time values.

# Functions Covered

| Function | Description |
|---|---|
| `YEAR()` | Extracts the year from a date |
| `MONTH()` | Extracts the month from a date |
| `DAY()` | Extracts the day from a date |
| `GETDATE()` | Returns the current date and time in SQL Server |
| `NOW()` | Returns the current date and time in MySQL |
| `DATEDIFF()` | Calculates the difference between two dates |
| `DATEADD()` | Adds or subtracts a specified date interval |

### Example 1: YEAR()

Extract the year from an order date.

```sql
SELECT
    Order_ID,
    Order_Date,
    YEAR(Order_Date) AS Order_Year
FROM Sales;
```

### Example 2: MONTH()

Extract the month from an order date.

```sql
SELECT
    Order_ID,
    MONTH(Order_Date) AS Order_Month
FROM Sales;
```

### Example 3: DAY()

Extract the day from an order date.

```sql
SELECT
    Order_Date,
    DAY(Order_Date) AS Order_Day
FROM Sales;
```

### Example 4: GETDATE()

Retrieve the current date and time in SQL Server.

```sql
SELECT GETDATE() AS Current_Date_Time;
```

### Example 5: DATEDIFF()

Calculate the number of days between two dates.

```sql
SELECT
    DATEDIFF(DAY, '2026-01-01', '2026-02-01')
    AS Date_Difference;
```

### Example 6: DATEADD()

Add seven days to a given date.

```sql
SELECT
    DATEADD(DAY, 7, '2026-11-03') AS Future_Date;
```

---

## 2. SQL String Functions

String Functions are built-in SQL functions used to manipulate, transform, extract, and clean text-based data.

### Functions Covered

| Function | Description |
|---|---|
| `UPPER()` | Converts text into uppercase |
| `LOWER()` | Converts text into lowercase |
| `LEN()` / `LENGTH()` | Calculates the length of a string |
| `CONCAT()` | Combines multiple strings |
| `SUBSTRING()` | Extracts a portion of a string |
| `TRIM()` | Removes leading and trailing spaces |
| `REPLACE()` | Replaces specific characters or text |
| `LEFT()` | Extracts characters from the left |
| `RIGHT()` | Extracts characters from the right |

### Example 1: UPPER()

Convert customer names into uppercase.

```sql
SELECT
    UPPER(Customer_Name) AS Upper_Name
FROM Customers;
```

### Example 2: LOWER()

Convert email addresses into lowercase.

```sql
SELECT
    LOWER(Email) AS Lower_Email
FROM Customers;
```

### Example 3: LEN()

Calculate the length of customer names in SQL Server.

```sql
SELECT
    Customer_Name,
    LEN(Customer_Name) AS Name_Length
FROM Customers;
```

### Example 4: CONCAT()

Combine first name and last name.

```sql
SELECT
    CONCAT(First_Name, ' ', Last_Name) AS Full_Name
FROM Employees;
```

### Example 5: SUBSTRING()

Extract a specific portion of a string.

```sql
SELECT
    SUBSTRING('DATA ANALYST', 1, 4) AS Result;
```

### Example 6: TRIM()

Remove unnecessary spaces.

```sql
SELECT
    TRIM(Customer_Name) AS Clean_Name
FROM Customers;
```

### Example 7: REPLACE()

Replace a specific text value.

```sql
SELECT
    REPLACE('Data Science', 'Science', 'Analytics')
    AS Updated_Text;
```

### Example 8: LEFT() and RIGHT()

Extract characters from the left and right sides.

```sql
SELECT
    LEFT('DATA ANALYST', 4) AS Left_Result,
    RIGHT('EMP101', 3) AS Right_Result;
```

---

## 3. Practical SQL Applications

### Monthly Sales Report

```sql
SELECT
    YEAR(Order_Date) AS Sales_Year,
    MONTH(Order_Date) AS Sales_Month,
    SUM(Amount) AS Total_Sales,
    COUNT(Order_ID) AS Total_Orders
FROM Sales
GROUP BY
    YEAR(Order_Date),
    MONTH(Order_Date)
ORDER BY
    Sales_Year,
    Sales_Month;
```

### Customer Data Cleaning

```sql
SELECT
    Customer_ID,
    UPPER(TRIM(Customer_Name)) AS Clean_Name,
    LOWER(Email) AS Clean_Email
FROM Customers;
```

### Calculate Days Since Order

```sql
SELECT
    Order_ID,
    Order_Date,
    DATEDIFF(DAY, Order_Date, GETDATE()) AS Days_Since_Order
FROM Sales;
```

---

## 4. Real-World Applications

I understood how these functions are used in practical Data Analyst tasks:

1. Monthly and yearly sales analysis.
2. Customer data cleaning and standardization.
3. Calculating delivery time and order duration.
4. Extracting information from employee IDs.
5. Standardizing email addresses.
6. Preparing customer reports.
7. Analyzing customer purchase patterns.
8. Generating date-based business reports.

---

## 5. Practice Questions

I practiced the following SQL problems:

### Date Functions
- Extract the year from employee joining dates.
- Extract the month and day from dates.
- Find employees who joined in a particular year.
- Calculate the number of days between two dates.
- Display the current date and time.
- Add 30 days to a given date.
- Generate a yearly employee joining report.

### String Functions
- Convert customer names into uppercase.
- Convert email addresses into lowercase.
- Calculate the length of customer names.
- Combine first and last names.
- Extract the first four characters of a string.
- Remove unnecessary spaces.
- Replace specific characters in email addresses.
- Extract employee ID numbers.

# 6. Key Learnings

- Learned how SQL Date Functions work.
- Understood date extraction using YEAR(), MONTH(), and DAY().
- Learned date calculations using DATEDIFF() and DATEADD().
- Understood how to manipulate text using String Functions.
- Learned how to standardize and clean customer information.
- Practiced combining multiple SQL functions.
- Understood how these functions help generate business reports.


