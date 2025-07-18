# KMS-Sales-Analysis

## Project Overview

Kultra Mega Stores (KMS), headquartered in Lagos, specializes in office supplies and furniture. Its customer base includes individual consumers, small businesses (retail), and large corporate clients (wholesale) across Lagos, Nigeria. I'm requested to analyze the data and present my key insights and findings. 

## Data Source

CSV file shared by Digital Skillup Africa (DSA)

## Tools Used

    Microsoft Excel
        - To Check Data accuracy and cleaning
    SQL
        - For Analysis and result finding

        
## Exploratory Data Analysis

EDA involved the exploring of the Data to answer some questions about the data such as;

### Case Scenario I
      1. Which product category had the highest sales?
      2. What are the top 3 and bottom 3 regions in terms of sales?
      3. What are the total sales of appliances in Ontario?
      4. Advice the management of KMS on what to do to increase the revenue from the bottom 10 customers
      5. KMS incurred the  ost shipping cost using which shipping mode?
### Case Scenario II
      6. Who are the most valuable customers, and what product or services do they typically purchase?
      7. Which small business customer has the highest sales?
      8. Which Corporate customer placed the most number of orders in 2009 - 2012?
      9. Which consumer customer was the most profitable one?
      10. Which customer returned items, and what segment do they belong to?
      11. If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping cost based on the order priority? Explain your answer
      
Data Analysis
This is where we include some basic lines of code or queries or even some of the DAX expressions used during your analysis

'''SQL
        create database KMS_db

SELECT * FROM KMS_db.DBO.[KMS Sql Case Study]

----WHICH PRODUCT CATEGORY HAD THE HIGHEST SALES?---

SELECT TOP 1
PRODUCT_CATEGORY,
SUM(SALES) AS TOTAL_SALES
FROM
KMS_db.DBO.[KMS Sql Case Study]
GROUP BY
Product_Category
ORDER BY
TOTAL_SALES DESC;


----TOP 3 REGIONS IN TERMS OF SALES----
SELECT TOP 3
REGION,
SUM(SALES) AS TOTAL_SALES
FROM
KMS_db.dbo.[KMS Sql Case Study]
GROUP BY
Region
ORDER BY
TOTAL_SALES DESC;

----BOTTOM 3 REGION IN TERMS OF SALES----
SELECT TOP 3
REGION,
SUM(SALES) AS TOTAL_SALES
FROM
KMS_db.dbo.[KMS Sql Case Study]
GROUP BY
Region
ORDER BY
TOTAL_SALES ASC;

----TOTAL SALES OF APPLIANCES IN ONTARIO-----
SELECT
SUM(SALES) AS TOTAL_SALES
FROM
KMS_db.dbo.[KMS Sql Case Study]
WHERE
Product_Sub_Category = 'APPLIANCES'
AND Province = 'ONTARIO';


---- BOTTOM 10 CUSTOMERS-----
SELECT TOP 10
CUSTOMER_NAME,
SUM(SALES) AS TOTAL_SALES
FROM
KMS_db.dbo.[KMS Sql Case Study]
GROUP BY
CUSTOMER_NAME
ORDER BY
TOTAL_SALES ASC;


----SHIPPING METHOD WITH HIGHEST COST----
SELECT TOP 1
SHIP_MODE,
SUM(SHIPPING_COST) AS TOTAL_SHIPPING_COST
FROM
KMS_db.dbo.[KMS Sql Case Study]
GROUP BY
Ship_Mode
ORDER BY
TOTAL_SHIPPING_COST DESC;


----BOTTOM 10 CUSTOMERS----
SELECT TOP 10
CUSTOMER_NAME,
SUM(SALES) AS TOTAL_SALES
FROM
KMS_db.dbo.[KMS Sql Case Study]
GROUP BY
Customer_Name
ORDER BY
TOTAL_SALES ASC;


----MOST VALUABLE CUSTOMER AND THEIR PURCHASES----
SELECT
CUSTOMER_NAME,
Product_Category,
SUM(SALES) AS TOTAL_SALES
FROM
KMS_db.dbo.[KMS Sql Case Study]
GROUP BY
Product_Category,
CUSTOMER_NAME
ORDER BY
TOTAL_SALES DESC;



----SMALL BUSINESS CUSTOMER WITH HGHEST SALES----
SELECT TOP 1
CUSTOMER_NAME,
SUM(SALES) AS TOTAL_SALES
FROM
KMS_db.dbo.[KMS Sql Case Study]
WHERE
Customer_Segment = 'SMALL BUSINESS'
GROUP BY
Customer_Name
ORDER BY
TOTAL_SALES DESC;


----CORPORATE CUSTOMER WITH MOST ORDERS (2009 -2012)-----
SELECT TOP 1
CUSTOMER_NAME,
COUNT(ORDER_ID) AS TOTAL_ORDERS
FROM
KMS_db.dbo.[KMS Sql Case Study]
WHERE
Customer_Segment = 'CORPORATE'
AND Order_Date BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY
Customer_Name
ORDER BY
TOTAL_ORDERS DESC;



----MOST PROFITABLE CONSUMER CUSTOMER----
SELECT TOP 1
CUSTOMER_NAME,
SUM(PROFIT) AS TOTAL_PROFIT
FROM
KMS_db.dbo.[KMS Sql Case Study]
WHERE
Customer_Segment = 'CONSUMER'
GROUP BY
Customer_Name
ORDER BY
TOTAL_PROFIT DESC;


----CUSTOMERS WHO RETURNED ITEMS AND THEIR SEGMENTS-----
---NO COLUMN SPECIFIEED ITEMS RETURNED---


----APPROPRIATENESS OF SHIPPING COSTS BASED ON ORDER PRIORITY----
SELECT
ORDER_PRIORITY,
SHIP_MODE,
AVG(SHIPPING_COST) AS AVERAGE_SHIPPING_COST
FROM
KMS_db.dbo.[KMS Sql Case Study]
GROUP BY
Order_Priority,
Ship_Mode
ORDER BY
Order_Priority,
AVERAGE_SHIPPING_COST DESC;
'''

## Result Finding/ Analysis

      1. Which product category had the highest sales?
        
          Technology had the highest sales of 5984248.18
          
      
      2. What are the top 3 and bottom 3 regions in terms of sales?

 ### Top 3
           REGION	TOTAL_SALES
            West	3597549.27
            Ontario	3063212.48
            Prarie	2837304.61

### Bottom 3
            REGION	                   TOTAL_SALES
            Nunavut                 	116376.48
            Northwest Territories	    800847.33
            Yukon	                    975867.38
      
      3. What are the total sales of appliances in Ontario?

          TOTAL_SALES of appliances is 202346.84


      4. Advice the management of KMS on what to do to increase the revenue from the bottom 10 customers

          Less revenue is generated from Furniture and Office supplies. I would advice they adopt a new method of advert and marketing or rebrand the product.
          
      5. KMS incurred the  most shipping cost using which shipping mode?

          KMS incured the most shipping cost using Delivery Truck

          SHIP_MODE	        TOTAL_SHIPPING_COST
          Delivery Truck	51971.94

      6. Who are the most valuable customers, and what product or services do they typically purchase?

          CUSTOMER_NAME	        Product_Category	        TOTAL_SALES
          Emily Phan	        Technology	                110481.97
          Deborah Brumfield	    Technology	                76795.79
          Dennis Kane	        Technology	                60434.64
          Jasper Cacioppo	    Technology	                57739.27
          Clytie Kelty	        Technology	                54454.95
          Raymond Book	        Technology	                53450.78
          Lisa DeCherney    	Furniture	                52477.37
          Alejandro Grove	    Office Supplies	            51696.02
          Grant Carroll        	Office Supplies	            50837.27
          Roy Skaria	        Furniture	                50177.24

          
      7. Which small business customer has the highest sales?

          CUSTOMER_NAME	    TOTAL_SALES
          Dennis Kane	    75967.59

          
      8. Which Corporate customer placed the most number of orders in 2009 - 2012?

            CUSTOMER_NAME	TOTAL_ORDERS
            Adam Hart	        27

            
      9. Which consumer customer was the most profitable one?

          CUSTOMER_NAME	        TOTAL_PROFIT
          Emily Phan	        34005.44

          
      10. Which customer returned items, and what segment do they belong to?

          There's no column showing return status of item.
          
      11. If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping cost based on the order priority? Explain your answer

          No, the company did not spend shipping cost based on the order priority because the delivery truck was/is actually the most expensive method of delivery.
          I think they did random selection or maybe had other factors they considered.
