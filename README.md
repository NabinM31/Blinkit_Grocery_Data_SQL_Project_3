# 🛒 Blinkit Grocery Data Analysis Project 🚀

<p align="center">
  <img src="logo.png" width="200" alt="Project Logo">
</p>





---

## 📢 About This Project
This repository contains an **SQL-based Blinkit Grocery Data Analysis** project. It involves analyzing grocery sales data from Blinkit to extract meaningful insights using SQL queries. The dataset includes details about product categories, sales, pricing, and customer behavior.

## 🎯 Objectives
✅ Perform data cleaning and transformation.  
✅ Analyze grocery product trends and sales distribution.  
✅ Extract insights about pricing, demand, and customer behavior.  
✅ Practice SQL queries for data-driven decision-making.  

---

## 📂 Dataset Overview
The dataset consists of:
- 🛍️ **Product Name**
- 🏷️ **Category**
- 💰 **Price**
- 📦 **Quantity Sold**
- 📊 **Total Sales**
- 📅 **Order Date**
- 👥 **Customer ID**
- 🌍 **Location**

---

## 🏛 Database Schema
The following schema represents the structure of the Blinkit dataset:

```sql
CREATE TABLE blinkit_data (
    product_id VARCHAR(50) PRIMARY KEY,
    product_name VARCHAR(255) NOT NULL,
    category VARCHAR(100),
    price DECIMAL(10,2),
    quantity_sold INT,
    total_sales DECIMAL(10,2),
    order_date DATE,
    customer_id VARCHAR(50),
    location VARCHAR(255)
);
```


---

## 📝 Queries Included
📌 **Key SQL Queries Covered:**
- 📊 **Total Sales by Product Category**  
- 🏆 **Top-Selling Products**  
- 📈 **Sales Trends Over Time**  
- 📍 **Location-Based Sales Analysis**  
- 💰 **Average Price Per Category**  
- 📅 **Monthly and Yearly Sales Breakdown**  
- 🛒 **Customer Purchase Behavior Analysis**  

---

## 🚀 Usage
💡 Modify and test the queries in your preferred SQL environment.  
📊 Extend the dataset by adding more Blinkit grocery data.  
⚡ Optimize queries for better performance.  

---

## Business Questions and Analysis
---
1. Write a SQL query to find total sales:
```sql
SELECT SUM(total_sales)AS total_sales 
FROM blinkit_data;

--show as million and CAST function for change the data type
SELECT CAST(SUM(total_sales)/1000000 AS DECIMAL(10,2))AS total_sales_in_millions 		
FROM blinkit_data;
```
----
2. Write a SQL query find out Average sales
```sql
SELECT CAST(AVG(total_sales) AS DECIMAL(5,2))AS average_sales		
FROM blinkit_data;
```
-----
3. Find no.of items: the total count of different items sold
```sql
SELECT item_type,
       COUNT(item_type )AS total_count		
FROM blinkit_data
GROUP BY item_type;
```
-----
4. Write a SQL query to find out Average Ratings for item sold
```sql
SELECT CAST(AVG(rating)AS DECIMAL(5,2))AS avg_ratings	
FROM blinkit_data;
```
-----
5. Write a SQL query to find total sales by Fat content
```sql
SELECT item_fat_content,
       CAST(SUM(total_sales)AS DECIMAL(10,2))AS  total_fat_content	
FROM blinkit_data
GROUP BY item_fat_content ;

--all other column
SELECT item_fat_content,
      COUNT(item_type )AS total_count,
      CAST(SUM(total_sales)AS DECIMAL(10,2))AS  total_fat_content,		
	    CAST(avg(total_sales)AS DECIMAL(10,2))AS  Avg_fat_content,		
	    CAST(AVG(rating)AS DECIMAL(5,1))AS avg_fat_ratings		
FROM blinkit_data
GROUP BY item_fat_content ;
```
----
6.Write a SQL query to find total sales by item type
``sql
SELECT item_type,
       CAST(SUM(total_sales)AS decimal(10,2)) AS Total_sales	
FROM blinkit_data
GROUP BY item_type
ORDER BY total_sales DESC;
```
---
7.Write a SQL query to Fat content by outlet for total sales
```sql
SELECT outlet_location_type,
       item_fat_content,
       CAST(SUM(total_sales)AS DECIMAL(10,2))AS total_sales
FROM blinkit_data
GROUP BY outlet_location_type,item_fat_content	
ORDER BY total_sales ASC;
```
----
8.Write a SQL query to find total sales by outlet establishment
```sql
SELECT outlet_establishment_year,
       CAST(SUM(total_sales)AS DECIMAL(10,2)) AS total_sales	
FROM blinkit_data
GROUP BY outlet_establishment_year
ORDER BY outlet_establishment_year ASC;
```
---
9.Write a SQL query to find the Percentage of sales by outlet size
```sql
SELECT outlet_size, 
       CAST(SUM(total_sales)AS DECIMAL(10,2)) AS Total_sales
FROM blinkit_data
GROUP BY outlet_size;

SELECT outlet_size, 
CAST(SUM(total_sales)AS DECIMAL(10,2)) AS Total_sales,
CAST((SUM(total_sales)*100.0)/ SUM(SUM(total_sales))OVER() AS DECIMAL(10,2)) AS  percentage_sales
FROM blinkit_data
GROUP BY outlet_size
ORDER BY total_sales DESC;
```
---
10.Write a SQL query to find the Sales by outlet Locations
```sql
SELECT outlet_location_type,
	   CAST(SUM(total_sales)AS DECIMAL(10,2)) AS total_sales,
	   CAST((SUM(total_sales)*100.0)/ SUM(SUM(total_sales))OVER() AS DECIMAL(10,2)) AS  percentage_sales,
	   CAST(avg(total_sales)AS DECIMAL(10,2))AS  Avg_fat_content,	
	   COUNT(*)AS no_of_items,
	   CAST(AVG(rating)AS DECIMAL(5,2))AS avg_fat_ratings
FROM blinkit_data
GROUP BY outlet_location_type
ORDER BY total_sales DESC;
```
----
11.Write a SQL query to All the metrics by outlet type
```sql
SELECT outlet_type,
       CAST(SUM(total_sales)AS DECIMAL(10,2)) AS total_sales,
	     CAST((SUM(total_sales)*100.0)/ SUM(SUM(total_sales))OVER() AS DECIMAL(10,2)) AS  percentage_sales,
	     CAST(avg(total_sales)AS DECIMAL(10,2))AS  Avg_fat_content,	
	     COUNT(*)AS no_of_items,
	     CAST(AVG(rating)AS DECIMAL(5,2))AS avg_fat_ratings
FROM blinkit_data
GROUP BY outlet_type
ORDER BY total_sales DESC;	   
```

---  
🎯 **Happy Querying!** 🎯

