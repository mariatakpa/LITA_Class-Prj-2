# Customer Segmentation for a Subscription Service 
---
## Project Overview

This project aims to analyze customer data for a subscription service to identify key customer segments, subscription patterns , and trends in cancellations and renewals.

The goal is to identify distinct customer groups based on behaviors, demographics,and preferences to tailor marketing strategies, personalize user experiences, and increase customer lifetime value. This segmentation will help the company focus resources efficiently, improve customer satisfaction, and ultimately enhance revenue.

The final deliverable is an interactive Power BI dashboard that visualizes the insights gained from the analysis.

---
### Project Objective
- Analyze customer demographics and purchasing patterns
- Segment customers based on purchase frequency, average spend, and preferred product categories
- Understand the impact of customer loyalty programs or promotions on sales.

The project consists of three main parts:
1. **Excel Analysis** : Initial data exploration and calculations of key metrics
2. **SQL Queries** :Date extraction and analysis using SQL to answer specific business questions.
3. **PowerBI Dashboard** : Visualization of insights in an interactive dashboard.
   
---
## Data Requirements
-**Dataset**: The data should include columns such as `Customer ID`, `Subscription Type`, `Region`,`SubscriptionDate`,and `Revenue`

-**Database** : For SQL analysis, load the data into SQL analysis, load the data into SQL Server to run queries.

---
### Project Tools
The following software tools are required:

- Microsoft Excel: For data exploration and initial metrics
- SQL Server: For SQL queries and data analysis
- Power BI : For building the interactive dashboard.

---
### Data Collection and Preparation
Data Collection:

* Internal Data: Collect customer data from internal sources like CRM systems, purchase history, and web analytics. Key attributes might include demographics(age, gender,
income level), behavioral data( purchase frequency , types of products purchased) and engagement metrics.

 - Data Cleaning: Handle missing values by either imputing them with mean/ median values or using other statistical methods, depending on the nature of the data.

-  Data Transformation: Create new features based on existing data , such as customer lifetime value(CLV), Average transaction amount or recency-frequency-monetary(RFM) scores.

  ---
  ### Exploratory Data Analysis
  EDA involves the exploration of data to answer some questions about the data such as;
  - What are the primary demographic characteristics of the customer base( e.g age distribution, gender balance, income segments)?
  - How do customer demographics correlate with purchasing behavior or engagement levels?
  - What is the average order value , and does it vary by customer segments?
  - How much do customers spend on average, and are there any significant differences among segments?


---
### Insights
The analysis provide insights into:
- Customer Segments: Understanding different subscription types and regional distribution
- Subscription Trends: Identifying popular subscription types and average subscription duration
- Cancellations and Renewals: Analyzing patterns in cancellations and long-term subscribers.
- Revenue Distribution: Observing revenue trends by subscription type and region.


---
### Data Analysis
This is where I included lines of queries during analysis;

```sql
create database LITA_DB

select * from [dbo].[customer data]

select Region , Count (CustomerID) AS TotalCustomer from [dbo].[customer data]
GROUP BY Region

select SubscriptionType , Count( CustomerID) AS TotalCustomer from [dbo].[customer data]
GROUP BY SubscriptionType
ORDER BY TotalCustomer DESC

Select customer_id from SubscriptionStart where status= Canceled from [dbo].[customer data]
WHERE CustomerID <= 180

select AVG  (CustomerID )AS avgduration
from [dbo].[customer data]

select subscriptiontype
SUM (Revenue) AS TotalRevenue from [dbo].[customer data]
GROUP BY SubscriptionType

select Region , count (canceled) as Total_cancellation from[dbo].[customer data]
where Canceled is not null
group by Region

select SUM ( CASE WHEN  SubscriptionType = 'Active'
THEN 1 ELSE 0 END ) AS Active_Subscription,
SUM( CASE WHEN SubscriptionType= 'Canceled '
THEN 1 ELSE 0 END ) AS Canceled_Subscription from [dbo].[customer data]
```

---
### Data Visualization

![Customer Segmentation Analysis](https://github.com/user-attachments/assets/be74e2a2-57fc-4326-817c-fc31def8bcbc)
