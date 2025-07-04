# <h1 style="text-align: center;"> DSA ASSIGNMENT 1 </h1>
## <h2 style="text-align: center;"> Company: Kultra Mega Stores Inventory </h2>
# 1. **The Project Structure**
# Company Overview
Kultra Mega Stores (KMS), headquartered in Lagos, specialises in office supplies and
furniture. Its customer base includes individual consumers, small businesses (retail), and
large corporate clients (wholesale) across Lagos, Nigeria.
# 2. Assignment Overview
You have been engaged as a Business Intelligence Analyst to support the Abuja division of
KMS. The Business Manager has shared an Excel file containing order data from 2009 to
2012 and has requested that you analyze the data and present your key insights and
findings. Apply your SQL skills from the DSA Data Analysis class and solve both case scenarios
as shared in the document.
# 3. Data Source
The main data used for this assignment was KMS sales data.csv and it was shared with us through the MLS channel using for our DSA Data Analysis Program. 
# Tools Used
- microsoft Excel [DOWNLOAD HERE](https://www.microsoft.com/en-us/microsoft-365/excel)
    - For data cleaning
    - For data visualization
- SQL Server [DOWNLOAD HERE](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
    - For data query
    - for data analysis
# Data Preparation and Cleaning
Firstly, to ensure KMS dataset is clean and robust before using, below actions were carried out;
1. Data loading and inspection
2. Handling missing values 
3. Data cleaning and formatting
## Case Scenario I
In this stage, Exploratory data analysis (EDA) was carried out by examined the datasets in order to provide answers to all the questions in this Case Scenario I.
## Data Analysis
This is where I performed some basic lines of code/queries used during the analysis and visualization of data.
### Question 1
*Which product category had the highest sales?* </br>
Before the analyses were conducted in SQL, the web application was launched, and a database was created to facilitate the analyses. Subsequently, the KMS sales case study dataset was imported, and all data types were appropriately set.
To address Question 1, the following SQL query was executed, and the results are displayed in the table below in a descending order to ensure that the highest salses based on product category was first reported.

``` SQL
select product_category, sum(sales) as [Total Sales]
from KMS
group by product_category
order by [total sales] desc
```
![Picture](https://github.com/user-attachments/assets/92d7293e-f66b-4c76-84b3-38d1909ff485)

### Question 2
*What are the Top 3 and Bottom 3 regions in terms of sales?* </br>
- FOR TOP 3 REGION IN TERM OF SALES

The SQL query below was executed and visualized as displayed below.</br>

``` SQL
select top 3 Region, sum(sales) as [Total Sales]
from KMS
group by Region
order by [total sales] desc
```
![Picture2](https://github.com/user-attachments/assets/9442b4d2-1491-45af-bdc4-ab20cbbb6ac8)

- FOR Bottom 3 REGION IN TERM OF SALES

The SQL query below was executed and visualized as displayed below.

```
select top 3 Region, sum(sales) as [Total Sales]
from KMS
group by Region
order by [total sales] asc
```
![BOTTOM](https://github.com/user-attachments/assets/d0f98874-5461-4cf4-860e-9defefe115c3)

### Question 3
*What were the total sales of appliances in Ontario?* </br>
The following SQL query comes up with the total sales of the products belonging to the sub-category 'appliances' in the region of Ontario using the KMS table. The expression SUM converts all the sales contents as per the requested condition (product_sub_category = 'appliances' and region = 'Ontario') and shows it as [Total Sales].
```
select sum(sales) as [Total Sales]
from KMS
where product_sub_category = 'appliances'
and region = 'ontario';
```
Total Sales = 202346.84

### Question 4
*Advise the management of KMS on what to do to increase the revenue from the bottom
10 customers* </br>
When recommending what KMS can do to increase their sales volume among the bottom 10 customers, various aspects such as order quantity, province, region, customer segment, product category and product sub-category were examined. In the analysis, it was realized that as much as some of these customers were geographically dispersed, their orders were solely done once with the core of the orders being related to office supplies. They were also primarily in the small businesses and corporate segments of customer see SLQ query below.
To tackle this, KMS is advised to:
**Improve customer engagement:** Establish better relationships by engaging with customers in a personalized way, and by using follow-ups.
**Provide targeted discounts:** Offer targeted discounts in the defence category of office supplies to encourage another buy.
**Encourage credit facilities:** Provide convenient payment schemes to the small businesses, as well as corporate clients.
**Customer survey:**  Conduct customer surveys to define and eliminate certain pain points in order to increase the level of meeting customer needs and expectations.

```
SELECT top 10
   customer_name, 
    SUM(sales) AS total_sales,
	SUM(order_quantity) AS total_order_quantity,
    province, 
    region, 
    customer_segment, 
    product_category, 
    product_sub_category
FROM 
	KMS
GROUP BY 
    customer_name,
	province, 
    region, 
    customer_segment, 
    product_category, 
    product_sub_category
ORDER BY 
    total_sales ASC
```
<img width="692" alt="p4" src="https://github.com/user-attachments/assets/bab548ff-e179-402f-80ff-318e74de9017" />

### Question 5
*KMS incurred the most shipping cost using which shipping method?* </br>
Value of shipping costs was initially rounded off to 2 decimal places in order to provide precision and consistency at all levels of analysis
```
SELECT * FROM KMS
alter table KMS
alter column shipping_cost decimal(10,2)
```
This SQL query performed a calculation of the total shipping cost using shipping mode in KMS table. It aggregates its data on the basis of the column ship_mode and aggregates shipping price using SUM. The output is then arranged in the order of increasing number of shipping cost with only the first row of the data being chosen.
```
select top 1
	ship_mode,
	sum(shipping_cost) As [Total Shipping Cost]
from 
	KMS
Group by
	ship_mode
order by 
	[Total Shipping Cost] desc
```
![Picture5](https://github.com/user-attachments/assets/b18ffc64-2ba1-4994-9a28-eb7efd2f8b5f)
## Case Scenario II
### Question 6
*Who are the most valuable customers, and what products or services do they typically
purchase?* </br>
The SQL statement extracts top 10 rows of customers contained in the KMS table with reference to their purchases. It summarizes information in customer_name, product_category and product_sub category. It finds the number of purchases and number of sales of every group. The outcomes are ranked based on customer name and the number of purchases in a decreasing pattern.

```
Select top 10
	customer_name,
	product_category,
	product_sub_category,
	count(*) As purchase_count,
	sum(sales) As [Total Sales]
from 
	KMS
where 
	customer_name IN (
Select
	customer_name
From
	KMS
	)
Group by 
	customer_name,
	product_category,
	product_sub_category
Order by 
	customer_name,
	purchase_count desc;
```
<img width="377" alt="p6" src="https://github.com/user-attachments/assets/f80e6e88-ecae-4ee1-afdd-c22fde1138e1" />

### Question 7
*Which small business customer had the highest sales?* </br>
This SQL selects the best customer on the small business segment of the KMS table based on the total sales. It rounds the amount of total sales per customer in this segment using SUM(sales), which groups the information in customer name. The results are ranked according to the total sales in descending order picking the highest.

```
select TOP 1
	customer_name,
	sum(sales) As [Total Sales]
From 
	KMS
Where
	customer_segment = 'small business'
Group by 
	customer_name
order by
	[Total Sales] desc
```
<img width="143" alt="p7" src="https://github.com/user-attachments/assets/cd9fc3cf-e5b3-48b0-9e2f-1292b01db33a" />

### Question 8
*Which Corporate Customer placed the most number of orders in 2009 – 2012?* </br>
This SQL query represents a name of the most frequent customer of the Corporate segment of the KMS table who ordered more during the period between January 1, 2009, and December 31, 2012. It splits data by customer_name, the order count takes count of how many orders the customers have (order_ID), and it returns the records in decreasing order of the total amount of orders and the top one is taken.
```
select TOP 1
	customer_name,
	COUNT(order_ID) As [Total Orders]
From 
	KMS
Where
	customer_segment = 'Corporate'
	AND order_date BETWEEN '2009-01-01' AND '2012-12-31'
Group by 
	customer_name
order by
	[Total Orders] desc
```
![Picture8](https://github.com/user-attachments/assets/535d0d02-b683-469b-981f-869539b58b51)

### Question 9
*Which consumer customer was the most profitable one?* </br>
The profit values were rounded to two decimal places first, to avoid rounding errors and be consistently rounded through the analysis. This is an important step in ensuring accurate outcomes and eliminating calculation and reporting discrepancies.
```
SELECT * FROM KMS
alter table KMS
alter column profit decimal(10,2)
```
This SQL query identifies the most profitable customer in the consumer segment of the KMS table. It groups data by customer_name and calculates the total profit for each customer using SUM(Profit). Results are sorted in descending order of total profit, and the top record with the highest profit is selected.
```
select top 1
	customer_name,
	SUM(Profit) AS [Total Profit]
FROM
	KMS
WHERE
	customer_segment = 'consumer'
GROUP BY
	customer_name
ORDER BY 
	[Total Profit] DESC
```
<img width="120" alt="p9" src="https://github.com/user-attachments/assets/6391121c-3cfa-4434-95b9-1f18a3b0dba2" />

### Question 10
*Which customer returned items, and what segment do they belong to?* </br>
The very first step is we need to combine the two table (the KMS employee table with Order Status table so that we can join which customers returned item and what segment does this customers belong to on a view table called VW_KMS_tbl. the query below represents the new table.
```
create view  VW_KMS_tbl
as
SELECT 
KMS.Row_ID,
[Order Status].Order_ID,
[Order Status].Status,
KMS.ORDER_DATE,
KMS.ORDER_PRIORITY,
KMS.ORDER_QUANTITY,
KMS.SALES,
KMS.DISCOUNT,
KMS.SHIP_MODE,
KMS.PROFIT,
KMS.UNIT_PRICE,
KMS.SHIPPING_COST,
KMS.CUSTOMER_NAME,
KMS.PROVINCE,
KMS.REGION,
KMS.CUSTOMER_SEGMENT,
KMS.PRODUCT_CATEGORY,
KMS.PRODUCT_SUB_CATEGORY,
KMS.PRODUCT_NAME,
KMS.PRODUCT_CONTAINER,
KMS.PRODUCT_BASE_MARGIN,
KMS.SHIP_DATE
FROM
[Order Status]
RIGHT JOIN KMS
ON
KMS.ORDER_ID = [Order Status].Order_ID
```
After joining the two tables the next step is to determine which customers returned items as well as the regions do they belong. An SQL query as queried below show the top 10 customers, customer segments, and total returns in descending order.
```
SELECT TOP 10
	customer_name,
	customer_segment,
	COUNT(order_ID) AS [Total_Returns]
FROM
	VW_KMS_tbl
WHERE
	Status = 'returned'
GROUP BY
	customer_name,
	customer_segment
ORDER BY
	[Total_Returns] desc;
```
<img width="254" alt="p10" src="https://github.com/user-attachments/assets/3997c3c4-e133-4d62-93f2-0b056c5d322d" />

### Question 11
*If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the Order Priority? Explain your answer.* </br>

In order to determine whether Kultra Mega Stores (KMS) arranged the shipping costs in compliance with Order Priority, there is a need to examine the use of shipping methods by various order priorities and whether high-priority orders employed faster/more costly options and low-priority ones slower/cheaper ones.
**Query: Shipping Method vs Order Priority**
```
SELECT 
    order_priority, 
    ship_mode, 
    COUNT(order_id) AS total_orders, 
    SUM(shipping_cost) AS [total shipping cost]
	FROM 
    KMS
GROUP BY 
    order_priority, 
    ship_mode
ORDER BY 
    order_priority, 
    [total shipping cost]DESC;
```
<img width="343" alt="P11" src="https://github.com/user-attachments/assets/e9435ddc-1447-4e29-89d0-0a91a0db4427" />

**ANSWER:** When shipping methods are always addressed according to order priority (i.e., low-priority orders use economical shipping methods versus high-priority orders use faster shipping methods), this demonstrates an efficient and adequate allocation priority to shipping costs. A mismatch with this alignment may indicate inefficiencies or wastage of resources.















