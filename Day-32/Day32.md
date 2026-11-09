# Day 32 – Power BI Interface, Visualizations & Basic Charts

## 1. Understanding the Power BI Interface

Power BI Desktop contains different sections that help us create and manage reports.

- **Ribbon:** Contains commands such as Get Data, Transform Data, Modeling, and Insert.
- **Report Canvas:** The main working area where we create and arrange visualizations.
- **Visualizations Pane:** Contains different charts and visual elements.
- **Data Pane:** Displays available tables, columns, and measures.
- **Filters Pane:** Allows us to filter data at different levels.

## 2. What is Data Visualization?

Data Visualization is the graphical representation of data using charts, graphs, tables, and other visual elements.

It helps Data Analysts identify trends, compare values, understand patterns, and communicate business insights.

**Example:** Instead of comparing sales figures for different cities manually, we can use a Bar Chart to identify the city with the highest sales.

## 3. Different Types of Power BI Visualizations

### A. Bar Chart
- Displays data using horizontal bars.
- Used to compare values across different categories.
- Example: Comparing sales across different cities.

### B. Column Chart
- Displays data using vertical bars.
- Used to compare products, departments, or yearly performance.
- Example: Comparing product-wise revenue.

### C. Line Chart
- Displays data using connected points and lines.
- Used to identify trends and changes over time.
- Example: Analyzing monthly sales growth.

### D. Pie Chart
- Displays data as circular slices.
- Shows the percentage contribution of different categories to a total.
- Example: Comparing product sales contributions.

### E. Donut Chart
- Similar to a Pie Chart but contains a hole in the center.
- Used to display category contributions and proportions.

### F. Table Visualization
- Displays information in rows and columns.
- Useful for showing detailed records and exact values.
- Example: Customer and order information.

### G. Matrix Visualization
- Displays summarized data using rows and columns.
- Supports grouping and hierarchical analysis.
- Example: City-wise and product-wise sales analysis.

### H. Card Visualization
- Displays a single important numerical value.
- Commonly used for KPIs (Key Performance Indicators).
- Example: Total Sales, Total Profit, and Total Orders.

### I. Slicer Visualization
- Allows users to interactively filter report data.
- Example: Selecting Hyderabad to display only Hyderabad sales.

## 4. Understanding Visual Fields

Power BI uses different fields to organize data inside visualizations.

- **X-axis:** Horizontal axis of a chart.
- **Y-axis:** Vertical axis of a chart.
- **Legend:** Separates different categories using colors.
- **Values:** Represents numerical information being measured.

These fields help Power BI understand how data should be displayed.

## 5. Understanding Aggregation

Aggregation means summarizing multiple values into a single result.

Important aggregation functions:

| Aggregation | Purpose |
|---|---|
| SUM | Adds all numerical values |
| AVERAGE | Calculates the average |
| COUNT | Counts values |
| MIN | Returns the smallest value |
| MAX | Returns the largest value |

**Example:**

Sales values: 50,000, 30,000, 20,000.

- SUM = 100,000
- AVERAGE = 33,333.33
- MIN = 20,000
- MAX = 50,000
- COUNT = 3

Choosing the correct aggregation is important for accurate business reporting.

## 6. Choosing the Correct Visualization

| Business Requirement | Recommended Visualization |
|---|---|
| Compare city-wise sales | Bar Chart |
| Compare product sales | Column Chart |
| Analyze monthly sales trends | Line Chart |
| Show percentage contribution | Pie / Donut Chart |
| Display detailed records | Table |
| Summarize grouped information | Matrix |
| Display total revenue | Card |
| Filter data by city or year | Slicer |

## 7. Practical Learning

I practiced working with sample sales data containing the following columns:

- OrderID
- Product
- City
- Quantity
- Price
- Sales

I explored how to:

1. Import Excel data into Power BI.
2. Create a Total Sales Card.
3. Create a City-wise Sales Bar Chart.
4. Create a Product-wise Column Chart.
5. Display sales information using a Table.
6. Apply City filters using a Slicer.
7. Understand how visualizations represent business information.

### Sales Calculation

**Formula:**

Sales = Quantity × Price

**Example:**

Quantity = 2

Price = 50,000

Sales = 2 × 50,000 = 100,000

## 8. Important Concepts Learned

- Power BI Desktop Interface
- Ribbon and Report Canvas
- Visualizations Pane
- Data Pane and Filters Pane
- Data Visualization
- Bar Chart and Column Chart
- Line Chart
- Pie Chart and Donut Chart
- Table and Matrix
- Card and Slicer
- X-axis and Y-axis
- Legend and Values
- Aggregation Functions
- Choosing Appropriate Visualizations

## 9. Key Takeaways

- Power BI provides different visualizations for analyzing business data.
- Bar and Column Charts help compare categories.
- Line Charts help identify trends over time.
- Pie and Donut Charts show contributions to a total.
- Tables and Matrices display detailed and summarized information.
- Cards display important business metrics.
- Slicers make reports interactive.
- Selecting the correct visualization improves report readability and decision-making.