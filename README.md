# LITA-CAPSTONE-Project-2
## Project Title: Customer Data
---

### INTRODUCTION
---
The dataset was provided by the institute to analyse the customer data for a subscription service to identify segments and trends.
#### Goals
- Identify Customer Behaivoior
- Track subscription types, 
- Identify key trends in cancellations and renewals and other key insights.

### Data Source 
---
The data used is provided by Incubator Hub. The data was provided in Excel workbook format, making it accessible for analysis.

### Tool used 
-	Microsoft EXCEL was used for the initial exploration of this dataset, clean and summaries 
- SQL- Structure Query Language was used for Querying of data
- Power BI was used for the visualization
- GitHub for Portfolio Building

### Data Cleaning and Preparation
---
  In the initial phase of Data cleaning and preparations, the following action were performened
  1. Data Inspection
  2. Data Cleaning and Formatting

### DATA STRUCTURE
---
The dataset contains: 
- Customer ID,
- Customer Name
- Subscription Start
- Subscription End
- Caanceled
- Revenue

### Exploratory Data Analysis
  ---
#### Key Performing Indicators (KPIs) used for this analysis include:
1. Analyze customer data to find subscription patterns. 
2. Identify the most popular subscription types
3. Find customers who canceled their subscription within 6 months.
4. Calculate the average subscription duration for all customers. 
5. Find customers with subscriptions longer than 12 months. 
6. Total revenue by subscription type. 
7. The top 5 customers by total purchase amount.
8. The top 3 regions by subscription cancellations.
9. Find the total number of active and canceled subscriptions.
    
### Data Analysis
Microsoft Excel
![Customer Dataset](https://github.com/user-attachments/assets/bbf4e58d-1ec8-43c7-952e-15dfa5c6124f)

### Visualization
![customer Dashboard](https://github.com/user-attachments/assets/7d9524c2-1b33-4660-8120-6103f5933fbf)

---
Some of the analyses and line of queries used includes;

- Microsoft Excel
Calculated the average subscription duration and identify the most popular 
subscription types.
![SQL QUERIES 2](https://github.com/user-attachments/assets/0b6688b2-0bc0-4277-b4a6-238669cfa896)

view the contents in the table
```sql
select* from[dbo].[LITA CustomerData 1]
```
1. retrieve the total number of customers from each region. 
```sql
SELECT REGION, COUNT(DISTINCT CUSTOMERID) AS TOTAL_CUSTOMERS
from[dbo].[LITA CustomerData 1]
GROUP BY REGION;
```
2. find the most popular subscription type by the number of customers. 
```sql
SELECT TOP 1 SUBSCRIPTIONTYPE, COUNT (DISTINCT CUSTOMERID) AS TOTAL_CUSTOMERS
FROM [dbo].[LITA CustomerData 1]
GROUP BY SUBSCRIPTIONTYPE ORDER BY TOTAL_CUSTOMERS DESC
```

3. find customers who canceled their subscription within 6 months. 
```sql
SELECT CUSTOMERID FROM[dbo].[LITA CustomerData 1]
WHERE DATEDIFF (MONTH,SUBSCRIPTIONSTART, SUBSCRIPTIONEND)<=6;
```

4. calculate the average subscription duration for all customers. 
```sql
SELECT AVG(DATEDIFF(DAY, SUBSCRIPTIONSTART, SUBSCRIPTIONEND)) AS AVG_SUBSCRIPTION_DURATION 
FROM[dbo].[LITA CustomerData]
```
5. find customers with subscriptions longer than 12 months. 
```sql
SELECT CUSTOMERID FROM[dbo].[LITA CustomerData 1]
WHERE DATEDIFF (MONTH,SUBSCRIPTIONSTART, SUBSCRIPTIONEND)>12;
```
6. calculate total revenue by subscription type. 

```sql
SELECT SUBSCRIPTIONTYPE,SUM(REVENUE) AS TOTAL_REVENUE FROM[dbo].[LITA CustomerData 1]
GROUP BY SUBSCRIPTIONTYPE;
```
7. find the top 3 regions by subscription cancellations. 

```sql
SELECT TOP 3 REGION, COUNT(*) AS SUBSCRIPTIONEND_COUNT 
FROM[dbo].[LITA CustomerData 1]
WHERE SUBSCRIPTIONEND IS NULL
GROUP BY REGION
ORDER BY SUBSCRIPTIONEND_COUNT DESC;
```
8. find the total number of active and canceled subscriptions. 
```sql
SELECT CANCELED, COUNT(DISTINCT CANCELED) AS CANCELED_SUBSCRIPTION
from[dbo].[LITA CustomerData 1]
GROUP BY CANCELED;
```


### Insights
#### types of suscription rom the data includes Basic, Premium and stamdard
##### Basic Subscription
- Basic has the largest number of suscribers,
- It has a total renenue of 33776735,
- It is mre common at East and North region.

##### Premium Subsciption
- It has a total renenue of 16864376,
- It is mre common at South region.
- it higher cancelation Rate
- it generate higher revenue per customer compared to Basic and Standard

##### Standard Subscription
- it is common at the west
- it has a total revenue of 16864376

#### Recommendation
- Impement customer retention packages for premium and standard customers to reduces high cancelation rate
- cancellation are lower at noth and east
