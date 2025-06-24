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
This is where carried out some basic lines of code/queries used during the analysis and visualization of data.
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
![Picture2b](https://github.com/user-attachments/assets/a9dcb4c9-a1af-44f0-8123-6b838a967884)

### Question 3
*What were the total sales of appliances in Ontario?* </br>
The following SQL query comes up with the total sales of the products belonging to the sub-category 'appliances' in the region of Ontario using the `KMS` table. The expression `SUM` converts all the sales contents as per the requested condition (`product_sub_category = 'appliances'` and `region = 'Ontario'`) and shows it as [Total Sales].
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






