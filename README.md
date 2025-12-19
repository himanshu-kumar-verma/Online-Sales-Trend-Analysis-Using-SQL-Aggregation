# Online Sales Trend Analysis Using SQL Aggregation

## 📌 Project Overview
This project focuses on analyzing **monthly sales trends** using SQL aggregation techniques.  
A cleaned online sales dataset was loaded into **SQLite**, and time based aggregations were performed to analyze **monthly revenue** and **order volume**.


## 🎯 Objective
- Analyze monthly revenue trends
- Analyze monthly order volume
- Identify time-based sales patterns using SQL


## 🗂 Dataset Description
The dataset contains cleaned online sales transaction records with the following key columns:

- `InvoiceNo` – Unique order identifier  
- `InvoiceDate` – Order date (MM/DD/YYYY format)  
- `TotalAmount` – Final transaction amount after discount and shipping  
- Additional columns related to products, customers, logistics, and returns  


## 🛠 Tools & Technologies
- **Database**: SQLite  
- **SQL Client**: DB Browser for SQLite  
- **Language**: SQL  


## 🧹 Data Preparation
The following steps were performed before analysis:

- Cleaned the dataset using Microsoft Excel
- Created a `TotalAmount` column using the formula:
  ```
  (Quantity × UnitPrice) × (1 − Discount) + ShippingCost
  ```
- Imported the cleaned dataset into SQLite
- Converted order dates to ISO format (`YYYY-MM-DD`) to enable accurate date-based aggregation


## 🧠 Key Challenge & Solution

### Challenge
SQLite treats dates as **TEXT** and does not directly parse the `MM/DD/YYYY` format using date functions.

### Solution
Dates were converted to ISO format using string functions before applying `strftime()` for year and month extraction.


## 📊 SQL Queries Used

### Monthly Revenue and Order Volume (All Years)
```sql
SELECT
strftime('%Y', InvoiceDate) AS year,
strftime('%m', InvoiceDate) AS month,
COUNT(DISTINCT InvoiceNo) AS order_volume
SUM(TotalAmount) AS monthly_revenue
FROM online_sales_dataset
GROUP BY year, month
ORDER BY year, month;
```


### Filter Sales for a Specific Year (Example: 2020)
```sql
SELECT
strftime('%Y', InvoiceDate) AS year,
strftime('%m', InvoiceDate) AS month,
COUNT(DISTINCT InvoiceNo) AS order_volume,
SUM(TotalAmount) AS monthly_revenue
FROM online_sales_dataset
WHERE strftime('%Y', InvoiceDate) = '2020'
GROUP BY year, month
ORDER BY year, month;
```


## 📈 Output
The final result table includes:
- Year
- Month
- Monthly order volume
- Monthly revenue

This output helps identify sales trends, seasonal patterns, and high performing months.


## ✅ Key Learnings
- Used `SUM()` for revenue aggregation
- Used `COUNT(DISTINCT ...)` for order volume calculation
- Applied `GROUP BY` for time-based analysis
- Handled SQLite date limitations effectively
- Understood the importance of ISO date formats


## 📂 Project Structure
- Dataset
  - Online_Sales_Dataset.csv
- Online_Sales_SQL_Analysis_Files
  - Online_Sales_Analysis.db
  - Online_Sales_Analysis.sqbpro

- Online_Sales_SQL_Analysis_Screenshots
- Readme.md


## 🚀 Future Enhancements
- Calculate month over month growth rate
- Analyze category wise monthly trends
- Compare sales and return patterns
- Visualize trends using Power BI or Excel


## 👤 Author
**Name**: Himanshu Kumar Verma

**Skills**: SQL | Excel | Data Analysis  

**GitHub**:
https://github.com/himanshu-kumar-verma

**LinkedIn**: 
https://www.linkedin.com/in/himanshu-kumar-verma2003
