# Day 43 - Data Cleaning and Analysis Using Python Pandas

##  Overview
Day 43 focuses on data cleaning and preparation using Python Pandas. Data cleaning is an important step in the data analysis process because real-world datasets often contain missing values, duplicate records, incorrect data types, and inconsistent information.

Before performing analysis or creating dashboards, a Data Analyst must ensure that the dataset is accurate and reliable.

##  Topics Covered

### 1. Data Cleaning
Data cleaning is the process of identifying and correcting errors in a dataset.

Common data problems include:
- Missing values
- Duplicate records
- Incorrect data formats
- Inconsistent text values
- Unusual values (Outliers)

### 2. Handling Missing Values
Missing values occur when some cells do not contain any information.

Pandas provides the following methods:

```python
df.isnull().sum()  # Identify missing values

df.dropna()        # Remove rows with missing values

df.fillna(0)       # Replace missing values with 0

df["Age"].fillna(df["Age"].mean())  # Replace missing age with average
```

**Importance:** Handling missing values helps improve data quality and prevents incorrect calculations.

### 3. Removing Duplicate Records
Duplicate records are repeated entries in a dataset.

```python
df.duplicated()       # Identify duplicate records

df.drop_duplicates()  # Remove duplicate records
```

**Importance:** Removing duplicates prevents incorrect counting and inaccurate analysis.

### 4. Correcting Data Types
Sometimes data is stored in an incorrect format.

Examples:
- Age stored as text instead of an integer.
- Salary stored as a string instead of a number.
- Date stored as text instead of a date format.

```python
df["Age"] = df["Age"].astype(int)

df["Date"] = pd.to_datetime(df["Date"])
```

**Importance:** Correct data types make calculations and analysis easier.

### 5. Handling Outliers
Outliers are unusually high or low values compared with other values in a dataset.

Example:

`25000, 28000, 30000, 32000, 500000`

Here, 500000 is an unusual salary value that needs investigation.

Common techniques:
- Interquartile Range (IQR)
- Box Plot
- Statistical Analysis

### 6. String Cleaning
String cleaning helps maintain consistency in text columns.

```python
df["Name"] = df["Name"].str.strip()

df["Name"] = df["Name"].str.lower()

df["Name"] = df["Name"].str.upper()
```

These methods remove unwanted spaces and standardize text values.

### 7. Merging Datasets
Merging combines two or more datasets using a common column.

```python
result = pd.merge(
    customers,
    orders,
    on="CustomerID",
    how="inner"
)
```

Types of joins:
- Inner Join - Returns matching records.
- Left Join - Returns all records from the left dataset.
- Right Join - Returns all records from the right dataset.
- Outer Join - Returns all records from both datasets.

##  Practical Learning

Practiced the following operations using Python Pandas:

1. Loading CSV files.
2. Identifying missing values.
3. Removing duplicate records.
4. Correcting data types.
5. Identifying outliers.
6. Cleaning text columns.
7. Merging multiple datasets.
8. Preparing cleaned data for analysis.

##  Importance of Data Cleaning

- Improves data accuracy.
- Reduces errors in analysis.
- Removes duplicate information.
- Maintains data consistency.
- Helps generate reliable reports.
- Prepares data for visualization and dashboards.

## Data Analysis Workflow

1. Raw Data Collection
2. Data Cleaning
3. Data Transformation
4. Data Analysis
5. Data Visualization
6. Generating Business Insights


