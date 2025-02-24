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

## 📖 Table of Contents
🔹 [Queries Included](#-queries-included)  
🔹 [Setup Instructions](#-setup-instructions)  
🔹 [Usage](#-usage)  
🔹 [License](#-license)  

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

## 📜 License
📌 This project is licensed under the **MIT License** – feel free to use and modify it.

📌 **🌟 Star this repo and follow for more SQL projects!** 🚀

---  
🎯 **Happy Querying!** 🎯

