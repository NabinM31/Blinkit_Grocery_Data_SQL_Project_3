DROP TABLE IF EXISTS blinkit_data;
CREATE TABLE blinkit_data(
           Item_Fat_Content VARCHAR(50),
	       Item_Identifier VARCHAR(50)NOT NULL,
		   Item_Type VARCHAR(50) NOT NULL,
		   Outlet_Establishment_Year INT NOT NULL,
		   Outlet_Identifier VARCHAR(50) NOT NULL,
		   Outlet_Location_Type	VARCHAR(50) NOT NULL,
		   Outlet_Size	VARCHAR(50)NOT NULL,
		   Outlet_Type	VARCHAR(50)NOT NULL,
		   Item_Visibility	FLOAT NOT NULL,
		   Item_Weight	FLOAT,
		   Total_Sales	FLOAT NOT NULL,
		   Rating FLOAT NOT NULL
);

SELECT * FROM blinkit_data;

--Need to update in item_fat_content
--LF,low fat ,reg to Low Fat and Regular in column one

UPDATE blinkit_data
SET item_fat_content=
CASE 
        WHEN item_fat_content IN ('LF', 'low fat') THEN 'Low Fat'		
        WHEN item_fat_content = 'reg' THEN 'Regular'
        ELSE item_fat_content  -- Keeps other values unchanged
    END;

--check distinct value now
SELECT DISTINCT item_fat_content FROM blinkit_data;

--1.Find total sales
SELECT SUM(total_sales)AS total_sales 
FROM blinkit_data;
--show as million using CAST function
SELECT CAST(SUM(total_sales)/1000000 AS DECIMAL(10,2))AS total_sales_in_millions 		
FROM blinkit_data;

--2.Find out Average sales
SELECT AVG(total_sales)AS average_sales
FROM blinkit_data;

SELECT CAST(AVG(total_sales)AS DECIMAL(5,2))AS average_sales --upto 2 decimal point		
FROM blinkit_data;

--3.Find no.of items: the total count of different items sold
SELECT item_type, COUNT(item_type )AS total_count		
FROM blinkit_data
GROUP BY item_type;

SELECT COUNT(item_type )AS total_count
FROM blinkit_data;

--4.Find out Average Ratings for item sold
SELECT AVG(rating)AS avg_ratings
FROM blinkit_data;

SELECT CAST(AVG(rating)AS DECIMAL(5,2))AS avg_ratings	
FROM blinkit_data;

SELECT * FROM blinkit_data;

--5.total sales by Fat content
SELECT item_fat_content	,SUM(total_sales)AS  total_fat_content
FROM blinkit_data
GROUP BY item_fat_content ;

SELECT item_fat_content,CAST(SUM(total_sales)AS DECIMAL(10,2))AS  total_fat_content	
FROM blinkit_data
GROUP BY item_fat_content ;

SELECT item_fat_content,
      COUNT(item_type )AS total_count,
      CAST(SUM(total_sales)AS DECIMAL(10,2))AS  total_fat_content,		
	  CAST(avg(total_sales)AS DECIMAL(10,2))AS  Avg_fat_content,		
	  CAST(AVG(rating)AS DECIMAL(5,1))AS avg_fat_ratings		
FROM blinkit_data
GROUP BY item_fat_content ;


--6.Find total sales by item type
SELECT item_type,CAST(SUM(total_sales)AS decimal(10,2)) AS Total_sales	
FROM blinkit_data
GROUP BY item_type
ORDER BY total_sales DESC;

--7.Fat content by outlet for total sales
SELECT outlet_location_type	item_fat_content,CAST(SUM(total_sales)AS DECIMAL(10,2))AS total_sales
FROM blinkit_data
GROUP BY outlet_location_type,item_fat_content	
ORDER BY total_sales ASC;

--8.total sales by outlet establishment
SELECT outlet_establishment_year,
      CAST(SUM(total_sales)AS DECIMAL(10,2)) AS total_sales,
      CAST(avg(total_sales)AS DECIMAL(10,2))AS  Avg_fat_content,		
	  CAST(AVG(rating)AS DECIMAL(5,2))AS avg_fat_ratings
FROM blinkit_data
GROUP BY outlet_establishment_year
ORDER BY outlet_establishment_year ASC;

--9.Percentage of sales by outlet size
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

SELECT * FROM blinkit_data;

--10.Sales by outlet Locations
SELECT outlet_location_type,
	   CAST(SUM(total_sales)AS DECIMAL(10,2)) AS total_sales,
	   CAST((SUM(total_sales)*100.0)/ SUM(SUM(total_sales))OVER() AS DECIMAL(10,2)) AS  percentage_sales,
	   CAST(avg(total_sales)AS DECIMAL(10,2))AS  Avg_fat_content,	
	   COUNT(*)AS no_of_items,
	   CAST(AVG(rating)AS DECIMAL(5,2))AS avg_fat_ratings
FROM blinkit_data
GROUP BY outlet_location_type
ORDER BY total_sales DESC;


--11.All the metrics by outlet type
SELECT outlet_type,
       CAST(SUM(total_sales)AS DECIMAL(10,2)) AS total_sales,
	   CAST((SUM(total_sales)*100.0)/ SUM(SUM(total_sales))OVER() AS DECIMAL(10,2)) AS  percentage_sales,
	   CAST(avg(total_sales)AS DECIMAL(10,2))AS  Avg_fat_content,	
	   COUNT(*)AS no_of_items,
	   CAST(AVG(rating)AS DECIMAL(5,2))AS avg_fat_ratings
FROM blinkit_data
GROUP BY outlet_type
ORDER BY total_sales DESC;	   




