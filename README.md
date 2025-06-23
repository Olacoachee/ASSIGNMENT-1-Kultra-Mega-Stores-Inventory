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
</br>
The SQL query below was executed and visualized as displayed below.
```
select top 3 Region, sum(sales) as [Total Sales]
from KMS
group by Region
order by [total sales] desc
```
![Picture2](https://github.com/user-attachments/assets/9442b4d2-1491-45af-bdc4-ab20cbbb6ac8)
- FOR Bottom 3 REGION IN TERM OF SALES
</br>
The SQL query below was executed and visualized as displayed below.
```
select top 3 Region, sum(sales) as [Total Sales]
from KMS
group by Region
order by [total sales] asc
```
![Picture2b](https://github.com/user-attachments/assets/a9dcb4c9-a1af-44f0-8123-6b838a967884)










