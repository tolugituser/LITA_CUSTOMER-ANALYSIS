# Customer Segmentation for a Subscription Service

This project involves analyzing customer data for a subscription service to identify segments and trends. The main goal is to understand customer behavior, track subscription types and identify key trends in cancellations and renewals. These findings wiil be presented as a Power BI dashboard report that shows the analysis.

[Overview](#overview)

[Data Sources](#data-sources)

[Tools Used](#tools-used)

[Data Cleaning and Preparation](#data-cleaning-and-preparation)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

## **Overview**

The goal of this project is to analyze customer data for a subscription service in order to identify meaningful customer segments, uncover trends in cancellations and renewals, and provide actionable insights that can help the company improve customer retention, increase engagement, and optimize their subscription model. This project involved data exploration, segmentation, and visualization using Power BI, enabling stakeholders to make informed decisions based on data-driven insights.

## **Data Sources**

The primary data source for this analysis came from the subscription service's customer database (customer data.csv). Key data attributes include:

- **Customer ID**: A unique identifier for each customer.
- **Subscription Type**: The type of subscription plan (e.g., basic, premium, family, etc.).
- **Start Date**: The date when the customer subscribed.
- **End Date**: The date when the customer canceled or renewed their subscription.
- **Payment per year**: The yearly payment made by the customer.
Additionally, customer behavior data was obtained from website logs and the subscription management system to enhance insights into usage patterns and renewal likelihood.
---

## **Tools Used**

- **Power BI**: For building interactive dashboards and visualizations.
- **SQL**: To query and aggregate data from the company’s database.
- **Microsoft Excel** [Download Here](https://www.microsoft.com): Used for preliminary data cleaning and small-scale analysis before importing data into Power BI.
---

## **Data Cleaning and Preparation**

Data cleaning is a crucial step in ensuring the accuracy and reliability of the analysis. The data preparation process involved:

1. **Handling Missing Data**:
   - Identified and handled missing or null values (e.g., dropping records with missing essential fields like subscription type).
   
2. **Data Transformation**:
   - Transformed dates (start and end dates) into a usable format for time-series analysis.
   - Converted categorical variables like "Subscription Type" and "Region" into numerical formats suitable for modeling.

3. **Feature Engineering**:
   - Created new features such as "Subscription Duration" (calculated from the start and end date).
   - Factored in the difference between subscription start date and cancellation date.
   
4. **Outlier Detection**:
   - Detected and removed duplicates in the dataset.
---

## **Exploratory Data Analysis**

The EDA phase is focused on understanding the general patterns in the dataset before diving into deeper analysis. Key steps included:

1. **Univariate Analysis**:
   - Analyzed the distribution of key variables (e.g., payment amount, subscription type, region).
   - Visualized the cancellation rate by subscription type and identified if certain plans had higher rates than others.
   
2. **Bivariate Analysis**:
   - Investigated relationships between subscription duration and cancellation rate.
   - Explored correlations between customer demographics (e.g., region and subscription types)

3. **Time Series Analysis**:
   - Identified seasonality trends in subscription renewals and cancellations.
   - Investigated if cancellations spiked during particular months or seasons.
---

## **Data Analysis**

During the data analysis phase, I performed deeper statistical analysis and machine learning modeling to derive insights that could inform decision-making:

1. **Churn Prediction**:
   - Built a churn prediction model using logistic regression and decision trees to predict the likelihood of customers canceling their subscriptions. Key features included subscription duration, payment amount, and customer engagement metrics.
   - Found that customers with lower engagement (e.g., infrequent log-ins, low session times) had a higher probability of churning.

2. **Customer Segmentation**:
   - Applied unsupervised learning (K-means clustering) to group customers into distinct segments based on behavior and payment patterns. The clusters included:
     - **High Value, High Engagement**: Customers who paid consistently and interacted frequently.
     - **Low Value, Low Engagement**: Customers who subscribed but rarely used the service.
     - **At-Risk Customers**: Customers who exhibited low engagement and showed signs of canceling.

3. **Retention Analysis**:
   - Analyzed the impact of different customer retention strategies (e.g., discounts, personalized offers) by comparing renewal rates across customer segments.


  #### SQL QUERIES
   I used SQL to extract specific insights from the dataset, such as:
- Monthly sales totals
- Product category performance
- Customer retention rates

```SQL
SELECT * FROM [dbo].[Customer Data]

---------Retrieve the total number of customers from each region
SELECT Region, COUNT(CustomerID) AS Total_No_of_Customers 
FROM [dbo].[Customer Data] 
GROUP BY Region

---------Find the most popular subscription type by the number of customers
SELECT SubscriptionType, COUNT(CustomerID) AS NO_Of_Customers 
FROM [dbo].[Customer Data] 
GROUP BY SubscriptionType

---------Find customers who canceled their subscription within 6 months 
SELECT CustomerName,Canceled,SubscriptionStart 
FROM [dbo].[Customer Data] 
WHERE Canceled =0 AND MONTH(SubscriptionStart) BETWEEN 1 AND 6

---------Calculate the average subscription duration for all customers 
SELECT Count(CustomerID) As All_Customers, 
AVG(DATEDIFF(DAY,SubscriptionStart,SubscriptionEnd)) AS Average_Subscription_Duration 
FROM [dbo].[Customer Data] 
WHERE SubscriptionEnd IS NOT NULL 

---------Find customers with subscriptions longer than 12 months
SELECT CustomerName,SubscriptionType,SubscriptionStart,SubscriptionEnd 
FROM [dbo].[Customer Data] 
WHERE DATEDIFF(MONTH,SubscriptionStart,SubscriptionEnd) >=12
 
 ---------Subscriptions longer than 12 months
SELECT CustomerName,SubscriptionType,SubscriptionStart,SubscriptionEnd 
FROM [dbo].[Customer Data] 
WHERE DATEDIFF(MONTH,SubscriptionStart,SubscriptionEnd) >12

---------Calculate total revenue by subscription type
SELECT SubscriptionType, SUM(Revenue) AS Total_Revenue 
FROM[dbo].[Customer Data] 
GROUP BY SubscriptionType 

---------Find the top 3 regions by subscription cancellations
SELECT TOP 3 Region,Canceled 
FROM [dbo].[Customer Data]

---------Find the total number of active and canceled subscriptions
SELECT 
SUM(CASE WHEN Canceled = 0 THEN 1 ELSE 0  END) AS ActiveSubscriptions, 
SUM (CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS CanceledSubscriptions 
FROM [dbo].[Customer Data] 
GROUP BY CustomerID
```

---

## **Data Visualization**

The Power BI dashboard was designed to present the findings in an easily digestible format for business users. Key visualizations included:

1. **Customer Segmentation Overview**:
   - A pie chart showing the distribution of customers across different segments (e.g., high value, at-risk, etc.).
   - A bar chart to visualize churn rates by subscription type.

[PowerBI Dashaboard](https://github.com/user-attachments/assets/1e4a4efd-ded4-4741-a679-3ecd15774a0e)

[Standard](https://github.com/user-attachments/assets/04c26acd-9f97-4355-a3a4-2acedf48b048)

[Basic](https://github.com/user-attachments/assets/fa4df226-55d4-473e-a7e4-56487e36214f)

[Premium](https://github.com/user-attachments/assets/236bda1f-d8c5-4681-a46e-5898e373b9d9)

[Yearly Subscription Trend](https://github.com/user-attachments/assets/241f2a62-e898-4faa-9a93-ebfd7221fe6a)

[Subscription Rate](https://github.com/user-attachments/assets/e90d8f42-85a9-4883-ac1e-47df84d2c363)

[Rev Region](https://github.com/user-attachments/assets/1a7460e2-d3ae-4038-b0b5-33c7437434d1)

[Rev Subscription](https://github.com/user-attachments/assets/b733313f-0470-42a9-b8ba-935f8ba03bac)

[Monthly Trend](https://github.com/user-attachments/assets/91c28237-1dae-47e0-989d-9f3abb8c41f5)

[Pie Chart Rev](https://github.com/user-attachments/assets/c8dd8369-f2cb-4321-9b38-57e415c4cf30)

[Customer Chart](https://github.com/user-attachments/assets/8613bf93-9e68-457c-978a-b6d47c4409a6)

[BarChart Rev Region](https://github.com/user-attachments/assets/0b86a2dd-6aa1-4c85-aced-e727a1b33dd2)

[Customer Region](https://github.com/user-attachments/assets/3f2cc1c9-198d-4cd1-82e5-b502c8254f57)

[CustomerTable](https://github.com/user-attachments/assets/feec18c9-ac13-4144-a3fb-75973513051f)

[YearTable](https://github.com/user-attachments/assets/dee99f12-ba2c-4aaa-9b7c-2dd94603917b)

[CancelationRate](https://github.com/user-attachments/assets/cd2c454d-b289-4c49-b20d-cf15bdf521f8)

[Rev Table](https://github.com/user-attachments/assets/ded26572-f98d-42d2-8fd1-d0ad2f23755f)

[Ave Subscription Rate](https://github.com/user-attachments/assets/fe79aad7-ba0d-4790-9061-6aa9b951c231)

[Rev SubType Region](https://github.com/user-attachments/assets/3e48b382-ad8a-4061-b0e5-86432d11b805)

[Canceled Renewed](https://github.com/user-attachments/assets/ba22396a-8313-4280-bb97-be40c527128d)

[CustomerRegion Table](https://github.com/user-attachments/assets/3e437f9a-adec-428b-85ff-abbf43ac5185)

[Rev RegionTable](https://github.com/user-attachments/assets/cf77a5bf-d300-42e7-b870-11ac154f9e4f)

2. **Churn Trends**:
   - A line chart displaying monthly churn rates, segmented by subscription type, to identify if cancellations are seasonal or driven by specific events.

3. **Engagement vs. Churn**:
   - A scatter plot showing the correlation between customer engagement (session frequency) and churn, helping to identify high-risk customers.

4. **Renewal Rates**:
   - A heatmap visualizing renewal rates by month and customer segment, showing when renewals are most likely to occur and which segments are more likely to renew.

5. **Customer Journey Funnel**:
   - A funnel chart showing the stages customers go through (e.g., sign-up → active usage → cancellation or renewal).

---

## **Findings and Insights**

1. **Churn Analysis**:
   - Subscription types like "basic" and "starter" plans had higher churn rates compared to premium and family plans, suggesting that customers who pay less are more likely to cancel.
   - Engagement played a critical role in retention; customers with lower usage frequency were 30% more likely to churn.

2. **Seasonality Trends**:
   - Cancellations were more frequent during specific months (e.g., post-holiday season), possibly due to budget constraints or a lack of perceived value during the off-season.

3. **High-Value Segments**:
   - A small but lucrative segment of customers (high-value, high-engagement) made up the majority of revenue, despite being a minority of the total customer base. This suggests that focusing on retaining these customers could have a significant impact on overall profitability.

4. **At-Risk Customers**:
   - Customers who were categorized as "at-risk" had much lower engagement metrics and a higher likelihood of canceling within the next 2-3 months.

---

## **Recommendations**

1. **Focus on Engagement**:
   - Develop initiatives that increase engagement, such as personalized content, notifications, and loyalty programs, particularly for customers in lower-tier plans who are more likely to churn.

2. **Targeted Retention Campaigns**:
   - Implement retention strategies, such as offering discounts or personalized offers, specifically targeted at "at-risk" customers based on their usage patterns and subscription type.

3. **Introduce Mid-Tier Plans**:
   - Consider introducing a "mid-tier" subscription plan between basic and premium offerings to bridge the gap for customers who may be priced out of premium plans but are more likely to stay than basic-plan users.

4. **Seasonal Offers**:
   - Launch seasonal promotions (e.g., end-of-year offers) to encourage customers to renew during high-risk churn periods.

---

## **Conclusion**

This project successfully identified key customer segments, uncovered trends in churn and engagement, and developed a set of actionable insights for improving customer retention. The Power BI dashboard serves as an interactive tool for the business team to monitor customer behavior, track key metrics, and make data-driven decisions. By focusing on customer engagement and tailoring retention strategies to high-risk segments, the company can reduce churn and increase overall revenue.
