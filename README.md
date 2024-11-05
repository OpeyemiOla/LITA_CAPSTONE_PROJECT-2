# LITA_CAPSTONE_PROJECT-2
Lita class project on customerdata subscription

### PROJECT OVERVIEW:
This report presents an analysis of total revenue across different subscription types and differnt regions, summarizing performance, identifying the highest-earning subscription type and regions, and providing insights and recommendations.

### Top Selling Products
Regional Performances 
Monthly Sales Trend 
PowerBI for visualization and storytelling

DATA DESCRIPTION
This dataset includes the following Columns:

CustomerId

CustomerName

Region

SubscrptionType

SubscrptionStart

SubscrptionEnd

Canceled

Revenue

- STATISTICS ABOUT THE DATASET:
  
- Number of Unique Customers: 33787
  
 no of subscription types: 6
 
Total Sales: 67,540,175.00

Total Region: 4

### METHODOLOGY
---
Data Collection The dataset for this analysis was provided by LITA_ The Incubator Hub for leaening and training purposes. The data was provided in Excel sheet [download Here] (https://canvas.instructure.com/files/273182802/download?download_frd=1)

- The excel sheet was used for calculation and creating pivot tables to summarize the average subscription duration and identify the most popular subscription types.
  
- The excel sheet was for easy importing of files into: SQL to write various queries
  
- Power BI to create dashboards using various charts (Donut Chart, piechart and clustered Column Chart)

### DATA ANALYSIS
---
Calculation in Excel Generating Total Sales =SUM(H2:H33788) Capture total sales as revenue

calculating average total sales =AVERAGE(H2:H33788) Capture sales data average by subscription

- Excel Chart
![image](https://github.com/user-attachments/assets/e38029d6-d87d-4fb1-82fa-8b19062aaaa6)


- Pivot Table

![image](https://github.com/user-attachments/assets/1986f6ff-784b-48d3-b67d-416e785fe744)


- Queries in SQL PROJECT 2

Project 2: Customer Segmentation for a Subscription Service

1.	retrieve the total number of customers from each region.
   
SELECT 
    Region,
    COUNT(CustomerID) AS Total_Customers
  	
FROM 
    [dbo].[CustomerData$]
  	
GROUP BY 
    Region
  	
ORDER BY 
    Total_Customers DESC;

3.	find the most popular subscription type by the number of customers.
   
SELECT TOP 1
    SubscriptionType, 
    COUNT(CustomerID) AS Total_Customers
  	
FROM 
    [dbo].[CustomerData$]
  	
GROUP BY 
    SubscriptionType
  	
   ORDER BY 
           Total_Customers DESC;

4.	find customers who canceled their subscription within 6 months.
   
SELECT 
    CustomerID,
    CustomerName,
    SubscriptionStart,
    SubscriptionEnd,
    Canceled,
    DATEDIFF(month, SubscriptionStart, SubscriptionEnd) AS Subscription_Duration
  	
FROM 
   [dbo].[CustomerData$]
  	
WHERE 
    Canceled = 1
  	
    AND DATEDIFF(month, SubscriptionStart, SubscriptionEnd) <= 6
  	
ORDER BY 
    Subscription_Duration ASC;

5.	calculate the average subscription duration for all customers.
   
SELECT 
    AVG(DATEDIFF(month, SubscriptionStart, SubscriptionEnd)) AS Average_Subscription_Duration
  	
FROM 
    dbo.CustomerData$
  	
WHERE 
   Canceled = 1;

6.	find customers with subscriptions longer than 12 months.
   
SELECT 
    CustomerID,
    CustomerName,
    SubscriptionStart,
    SubscriptionEnd,
    DATEDIFF(month, SubscriptionStart, SubscriptionEnd) AS Subscription_Duration
  	
FROM 
    dbo.CustomerData$
  	
WHERE 
    DATEDIFF(month, SubscriptionStart, SubscriptionEnd) > 12
  	
      AND Canceled = 0;

7.	calculate total revenue by subscription type.
   
SELECT 
    SubscriptionType,
    SUM(Revenue) AS Total_Revenue
  	
FROM 
    dbo.CustomerData$
  	
GROUP BY 
    SubscriptionType
  	
ORDER BY 
    Total_Revenue DESC;

8.	find the top 3 regions by subscription cancellations.
   
SELECT TOP 3 
    Region,
    COUNT(CustomerID) AS Cancellation_Count
  	
FROM 
    dbo.CustomerData$
  	
WHERE 
    Canceled = 1
  	
GROUP BY 
    Region
  	
ORDER BY 
   Cancellation_Count DESC;


9.	find the total number of active and canceled subscriptions.
   
SELECT 
    SUM(CASE WHEN Canceled = 0 THEN 1 ELSE 0 END) AS Active_Subscriptions,
    SUM(CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS Canceled_Subscriptions
  	
FROM 
  dbo.CustomerData$;




-SQL VISUALS image

![image](https://github.com/user-attachments/assets/2562afd3-c4a2-4aae-89dd-81fe09769e7f)


![image](https://github.com/user-attachments/assets/b61cca34-6b77-435b-acc3-bea96a3c2bda)


![image](https://github.com/user-attachments/assets/10f266ab-089d-4826-9dd0-a9320ddeac42)



DASH BOARD OVERVIEW WITH POWER BI:
image

image

image

### Data Summary
---
The data outlines the revenue figures by region and by subscription type. Here’s the breakdown:

- Revenue by Region:

East: NGN 16,958,763.00

North: NGN 16,817,972.00

South: NGN 16,899,064.00

West: NGN 16,864,376.00

Grand Total: NGN 67,540,175.00

- Revenue by Subscription Type:

Basic: NGN 33,776,735.00

Premium: NGN 16,899,064.00

Standard: NGN 16,864,376.00

Grand Total: NGN 67,540,175.00

### Key Insights:
---

Top Performing Region:

East region leads slightly with NGN 16,958,763.00, closely followed by South and North regions.

Top Performing Subscription Type:

The Basic subscription dominates, accounting for 50.0% of the total revenue.

Balanced Regional Distribution:

Revenue is almost evenly distributed across all four regions, indicating a well-balanced performance.

Subscription Type Contribution:

Basic subscription significantly contributes to the total revenue, with Premium and Standard being evenly matched.

### Recommendations:
---

Maintain Regional Balance:

Continue to maintain balanced efforts across all regions to sustain the even distribution of revenue.

Boost Premium and Standard Subscriptions:

Focus on enhancing marketing and sales strategies for Premium and Standard subscriptions to increase their uptake. Emphasize the unique benefits of these plans.

Targeted Promotions:

Create targeted promotional campaigns for each region, taking into account any regional preferences and trends.

Customer Feedback:

Regularly gather and analyze customer feedback from different regions and subscription types to understand their needs and improve offerings.

Incentivize Upgrades:

Offer incentives for Basic subscribers to upgrade to Premium or Standard subscriptions, such as special features or discounts.

### Conclusion 
---
The analysis reveals a balanced regional revenue distribution and a dominant Basic subscription. The insights and recommendations provided can help optimize sales strategies and improve overall performance across different regions and subscription types.
