# Customer Segmentation for a Subscription Service 
This project involves analyzing customer data for a subscription service to identify segments and trends. Your goal is to understand customer behavior, track subscription types and identify key trends in cancellations and renewals. The final deliverable is a Power BI dashboard that presents your analysis.

### **Overview**

The goal of this project was to analyze customer data for a subscription service in order to identify meaningful customer segments, uncover trends in cancellations and renewals, and provide actionable insights that can help the company improve customer retention, increase engagement, and optimize their subscription model. This project involved data exploration, segmentation, and visualization using Power BI, enabling stakeholders to make informed decisions based on data-driven insights.

## **Data Sources**

The primary data source for this analysis came from the subscription service's customer database. Key data attributes include:

- **Customer ID**: A unique identifier for each customer.
- **Subscription Type**: The type of subscription plan (e.g., basic, premium, family, etc.).
- **Start Date**: The date when the customer subscribed.
- **End Date**: The date when the customer canceled or renewed their subscription.
- **Payment Amount**: The monthly payment made by the customer.
- 
---
**Churn Indicator**: A binary flag (0 = active, 1 = churned).
- **Customer Demographics**: Information such as age, location, and gender.
- **Engagement Metrics**: Data on how often customers interact with the service (e.g., usage frequency, session length, etc.).

Additionally, customer behavior data was obtained from website logs and the subscription management system to enhance insights into usage patterns and renewal likelihood.

---

## **Tools Used**

- **Power BI**: For building interactive dashboards and visualizations.
- **SQL**: To query and aggregate data from the company’s database.
- **Excel**: Used for preliminary data cleaning and small-scale analysis before importing data into Power BI.
- **Python** (Optional): Used for more advanced data analysis and statistical modeling (e.g., clustering algorithms).
- **Jupyter Notebooks**: For conducting exploratory data analysis (EDA) and generating Python scripts if required.

---

## **Data Cleaning and Preparation**

Data cleaning is a crucial step in ensuring the accuracy and reliability of the analysis. The data preparation process involved:

1. **Handling Missing Data**:
   - Identified and handled missing or null values (e.g., using imputation techniques or dropping records with missing essential fields like subscription type).
   
2. **Data Transformation**:
   - Transformed dates (start and end dates) into a usable format for time-series analysis.
   - Converted categorical variables like "Subscription Type" and "Region" into numerical formats suitable for modeling.

3. **Feature Engineering**:
   - Created new features such as "Subscription Duration" (calculated from the start and end date).
   - Developed "Churn Duration" as the difference between subscription start date and cancellation date.
   
4. **Outlier Detection**:
   - Detected and removed outliers in financial data, such as unusually high payment amounts that were likely errors.

5. **Normalization**:
   - Applied scaling techniques to customer engagement metrics to standardize the data, making it easier to compare different customer segments.

---

## **Exploratory Data Analysis (EDA)**

The EDA phase focused on understanding the general patterns in the dataset before diving into deeper analysis. Key steps included:

1. **Univariate Analysis**:
   - Analyzed the distribution of key variables (e.g., payment amount, subscription type, age).
   - Visualized the churn rate by subscription type and identified if certain plans had higher churn rates than others.
   
2. **Bivariate Analysis**:
   - Investigated relationships between subscription duration and churn rate.
   - Explored correlations between customer demographics (e.g., age, gender) and subscription types or churn.

3. **Time Series Analysis**:
   - Identified seasonality trends in subscription renewals and cancellations.
   - Investigated if cancellations spiked during particular months or seasons.
   
4. **Segmentation**:
   - Used clustering techniques (e.g., K-means) to segment customers based on their engagement level, payment history, and subscription type. This helped uncover distinct customer profiles (e.g., "high engagement" vs "low engagement").

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
   
---

## **Data Visualization**

The Power BI dashboard was designed to present the findings in an easily digestible format for business users. Key visualizations included:

1. **Customer Segmentation Overview**:
   - A pie chart showing the distribution of customers across different segments (e.g., high value, at-risk, etc.).
   - A bar chart to visualize churn rates by subscription type.

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
