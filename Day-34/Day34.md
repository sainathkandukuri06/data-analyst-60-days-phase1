# Day 34 – Data Modeling in Power BI

Data Modeling is the process of organizing, connecting, and managing multiple tables in Power BI to create meaningful reports and dashboards.

It helps Data Analysts combine data from different sources, reduce data duplication, improve report performance, and generate accurate business insights.

## 1. Primary Key and Foreign Key

### Primary Key (PK)
- A Primary Key uniquely identifies each record in a table.
- It cannot contain duplicate values.
- Example: CustomerID in the Customers table.

### Foreign Key (FK)
- A Foreign Key connects one table to another table.
- It references the Primary Key of another table.
- Example: CustomerID in the Orders table.

**Difference:**
- Primary Key: Uniquely identifies a record.
- Foreign Key: Establishes a relationship between tables.

## 2. Relationships in Power BI

Relationships connect two or more tables using common columns.

They allow Power BI to retrieve related information from different tables without manually combining all the data.

### Types of Relationships (Cardinality)

**1. One-to-One (1:1)**
- One record in Table A matches one record in Table B.
- Example: One employee and one employee profile.

**2. One-to-Many (1:Many)**
- One record in Table A can match multiple records in Table B.
- Example: One customer can place multiple orders.
- This is commonly used in Power BI.

**3. Many-to-One (Many:1)**
- Multiple records in one table connect to one record in another table.
- Example: Multiple orders belong to one customer.

**4. Many-to-Many (Many:Many)**
- Multiple records in one table can connect to multiple records in another table.
- Example: Students and courses.

## 3. Fact Table

A Fact Table stores measurable business data and transaction details.

Examples:
- Sales Amount
- Quantity
- Profit
- Revenue
- Transaction Details

Fact tables generally contain Foreign Keys that connect them to Dimension Tables.

## 4. Dimension Table

A Dimension Table stores descriptive information used to analyze business data.

Examples:
- Customer Details
- Product Details
- Employee Details
- Location Details
- Date Information

**Difference:**
- Fact Table: Stores measurable business information.
- Dimension Table: Stores descriptive business information.

## 5. Star Schema

A Star Schema is a data modeling technique in which one central Fact Table connects to multiple Dimension Tables.

### Example:
- FactSales – Stores sales transactions.
- DimCustomer – Stores customer information.
- DimProduct – Stores product information.
- DimDate – Stores date information.
- DimStore – Stores store information.

### Advantages of Star Schema
1. Easy to understand and maintain.
2. Improves report performance.
3. Simplifies DAX calculations.
4. Reduces unnecessary data duplication.
5. Makes report development easier.

## 6. Creating Relationships in Power BI

Steps:
1. Open Power BI Desktop.
2. Import the required tables.
3. Navigate to Model View.
4. Identify common columns between tables.
5. Drag the Primary Key column onto the corresponding Foreign Key column.
6. Verify the relationship cardinality.
7. Select the appropriate cross-filter direction.
8. Apply the relationship.

## 7. Practical Business Example

Imagine working as a Data Analyst in an e-commerce company.

Your manager asks you to generate a report showing total sales by customer and product category.

Required tables:
- FactSales
- DimCustomer
- DimProduct

After creating relationships between these tables, we can analyze sales by customer and product category.

### DAX Measure

```dax
Total Sales = SUM(FactSales[Sales])
```

This measure calculates the total sales amount from the FactSales table.

## 8. Key Learnings

| Concept | Description |
|---|---|
| Data Modeling | Organizing and connecting tables |
| Primary Key | Uniquely identifies records |
| Foreign Key | Connects related tables |
| Relationships | Connect multiple tables |
| Cardinality | Defines relationship types |
| Fact Table | Stores measurable data |
| Dimension Table | Stores descriptive data |
| Star Schema | Fact table connected to dimension tables |

