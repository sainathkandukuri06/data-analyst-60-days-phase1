# Day 35 – Connecting SQL Server to Power BI

## 1. What is SQL Server?

SQL Server is a Relational Database Management System (RDBMS) developed by Microsoft.

It is used to store, organize, manage, and retrieve structured data.

**Example:**

Consider a company that maintains employee information in a database.

| Employee_ID | Employee_Name | Department | Salary |
|---|---|---|---:|
| 101 | Ravi | IT | 30000 |
| 102 | Kumar | HR | 25000 |
| 103 | Priya | Finance | 40000 |
| 104 | Sneha | IT | 35000 |

We can retrieve employee information using SQL queries.

```sql
SELECT * FROM Employees;
```

**Key Points:**
- Stores data in tables.
- Supports SQL queries.
- Manages large amounts of structured data.
- Helps retrieve and update information.
- Maintains relationships between tables.

---

## 2. What is Power BI SQL Server Connection?

Power BI provides a built-in SQL Server connector that allows users to connect directly to SQL Server databases.

Instead of manually exporting database information into Excel, we can connect Power BI to SQL Server and use the required data for analysis.

**Example:**

A retail company stores thousands of sales records in SQL Server. A Data Analyst connects Power BI to the sales database and creates a dashboard showing:

- Total Sales
- Total Profit
- Monthly Revenue
- Top-Selling Products
- Regional Sales Performance

This makes business analysis easier and faster.

---

## 3. Import Mode vs DirectQuery

Power BI provides two important connectivity modes when connecting to SQL Server.

### A. Import Mode

Import Mode copies data from SQL Server into the Power BI data model.

**How it works:**
1. Power BI connects to SQL Server.
2. It retrieves the selected data.
3. The data is loaded into Power BI.
4. Reports use the imported data.

**Advantages:**
- Faster report performance in many cases.
- Supports a wide range of Power BI features.
- Data can be analyzed without querying SQL Server for every interaction.

**Disadvantage:**
- Data must be refreshed to retrieve the latest changes from SQL Server.

### B. DirectQuery

DirectQuery keeps the data in the original SQL Server database. Power BI sends queries to the database when report data is requested.

**Advantages:**
- Data stays in the source database.
- Can access recent source data without importing the entire dataset.
- Useful when data is very large or source data needs to remain centrally managed.

**Disadvantages:**
- Report performance depends on database performance and network connectivity.
- Some Power BI features have limitations.

### Difference Between Import and DirectQuery

| Feature | Import Mode | DirectQuery |
|---|---|---|
| Data Storage | Power BI | SQL Server |
| Performance | Usually faster | Depends on source |
| Data Updates | Requires refresh | Queries source |
| Best Use | Many analytical reports | Large or frequently changing datasets |

---

## 4. Steps to Connect SQL Server to Power BI

1. Open Power BI Desktop.
2. Click on **Home → Get Data**.
3. Select **SQL Server**.
4. Enter the SQL Server name.
5. Enter the database name (optional).
6. Select Import or DirectQuery.
7. Click OK.
8. Provide the required authentication details.
9. Select the tables you want to analyze.
10. Click Load.

After loading, the selected SQL Server tables become available in Power BI.

---

## 5. What is Power Query?

Power Query is a data transformation and preparation tool available in Power BI.

It helps clean raw data before using it in reports and dashboards.

**Common Power Query Operations:**

- Remove Duplicates – Removes repeated records.
- Remove Columns – Deletes unnecessary columns.
- Replace Values – Replaces unwanted or incorrect values.
- Change Data Type – Converts text, numbers, and dates into correct formats.
- Filter Rows – Displays only the required records.
- Handle Null Values – Helps manage missing data.

**Example:**

If an employee table contains duplicate employee records, Power Query can remove duplicate rows before building the report.

---

## 6. Data Flow from SQL Server to Power BI

A typical Data Analyst workflow:

1. **SQL Server:** Stores company information.
2. **Power BI Connection:** Retrieves data from SQL Server.
3. **Power Query:** Cleans and transforms the data.
4. **Data Modeling:** Creates relationships between tables.
5. **DAX:** Creates calculations and measures.
6. **Visualization:** Builds charts, tables, and dashboards.

**Workflow:**

SQL Server → Power BI → Power Query → Data Modeling → DAX → Dashboard

---

## 7. Practical Example

**Scenario: Employee Salary Analysis**

Imagine a company has an employee database containing employee names, departments, and salaries.

A Data Analyst connects the database to Power BI and creates a report to understand salary distribution.

Possible analysis:
- Total Employee Count
- Average Salary
- Highest Salary
- Department-Wise Salary
- Employee Count by Department

Example SQL query:

```sql
SELECT
    Department,
    AVG(Salary) AS Average_Salary
FROM Employees
GROUP BY Department;
```

This query calculates the average salary for each department.

The results can be visualized using a bar chart in Power BI.

---

## 8. Important Concepts Learned

| Concept | Description |
|---|---|
| SQL Server | Stores and manages database information |
| SQL Connector | Connects Power BI to SQL Server |
| Import Mode | Loads data into Power BI |
| DirectQuery | Queries data from the original database |
| Power Query | Cleans and transforms data |
| Data Modeling | Organizes tables and relationships |
| DAX | Creates calculations and measures |
| Dashboard | Displays business information visually |

---

## 9. Key Learnings

After completing Day 35, I understood:

- What SQL Server is and how it stores data.
- How to connect SQL Server to Power BI.
- The difference between Import Mode and DirectQuery.
- How Power Query prepares data for analysis.
- How database information moves into Power BI reports.
- How SQL queries can support business analysis.

---

## 10. Conclusion

Connecting SQL Server to Power BI is an important skill for Data Analysts.

SQL Server helps store and manage business data, while Power BI helps analyze and visualize that information.

By combining SQL Server and Power BI, Data Analysts can create meaningful reports, identify business trends, and support better decision-making.

**Day 35 Completed – Learning SQL Server Connectivity with Power BI.**

---

### Technologies & Tools Used
- Microsoft SQL Server
- SQL
- Microsoft Power BI Desktop
- Power Query

### Tags
#DataAnalytics #PowerBI #SQLServer #SQL #PowerQuery #DataVisualization #Day35