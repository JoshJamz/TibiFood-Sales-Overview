# TibiFood-Sales-Overview
## Table of Content 


- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Tools](#tools) 
- [Project Objectives](#project-objectives)
- [Approach](#approach)
- [Exploratory Data Analysis EDA and Key Findings](#exploratory-data-analysis-eda-and-key-findings)
- [Data Analysis](#data-analysis)
- [Conclusion](#conclusion)


### Project overview  

This project involves conducting a comprehensive data analysis and business review for Tibi Foods, a fictional quick service restaurant chain store operating in Nigeria. The analysis focuses on extracting meaningful insights from a dataset containing information on successful and rejected orders from the last two quarters.

### Data Source

The dataset comprises data from Tibi Foods' operations on Chowdeck, an online platform for ordering meals. It includes details such as order creation times, delivery times, acceptance times, pick-up times, and other relevant metrics. Please note that this dataset is fabricated for the purpose of this analysis and does not represent real order data.

### Tools 
- Microsoft Excel
- SQL
- Power Bi

### Project Objectives

- Provide an overview of Tibi Foods' current business status.
- Evaluate Tibi Foods' performance in Q4 2023 relative to Q3 2023.
- Offer recommendations to help Tibi Foods improve and grow their revenue based on the insights derived from the dataset.

### Approach

- Data Cleaning: Utilized MS Excel for data cleaning tasks, including removing duplicates,handling missing values and formatting data for analysis.
- Data Exploration: Used SQL queries to interrogate the cleaned dataset and explore various metrics such as GMV (Gross Merchandise Value), order count, delivery time,pickup time, wait time, successful delivery percentage, and more.
- Visualization: Created clear and compelling visualizations using Power BI to present the findings of the analysis effectively. These visualizations includes interactive dashboards and reports to provide stakeholders with actionable insights.

### Exploratory Data Analysis EDA and Key Findings

- Conducted comprehensive EDA using SQL queries and Excel to explore various aspects of Tibi Foods' business operations.
- Analyzed  Total Order, order creation times, average ordered value, Total Revenue, delivery times, acceptance times, pick-up times,wait time and other relevant metrics to understand the overall performance.
- Identified trends and patterns in order volumes, delivery times, and successful delivery rates across different quarters.
- Examined the distribution of delivery times and acceptance times to identify outliers and potential areas for improvement in operational efficiency.
- Investigated the relationship between order success rates and factors such as delivery time and pick-up time to understand their impact on customer satisfaction.
- Utilized Power BI to visualize key metrics and trends, including GMV, order count, and successful delivery percentage, providing stakeholders with actionable insights.
- Discovered a slight decrease in order volumes in Q4 2023 compared to Q3 2023, indicating a potential need for targeted marketing efforts to boost sales.
- Observed a decrease in successful delivery rates in certain locations, suggesting the need for improved logistics and delivery management strategies.
- Identified a correlation between longer delivery times and higher order cancellations, highlighting the importance of optimizing delivery processes to reduce wait times.
- Recommended implementing strategies to streamline order processing, improve delivery efficiency, and enhance customer satisfaction based on the key findings from the EDA.

Through EDA, I gained valuable insights into Tibi Foods' business performance and identified areas for optimization to drive revenue growth and operational excellence.

### Data Analysis 
```  Sql
Select *
From [Tibi Food Dataset]

SELECT COUNT(*) AS total_orders
FROM [Tibi Food Dataset];

SELECT SUM(Order_Total_Gross) AS total_gmv
FROM [Tibi Food Dataset];

SELECT COUNT(*) AS total_orders
FROM [Tibi Food Dataset]
WHERE DATEPART(QUARTER, order_create_date) = 3 -- For Q3 2023

SELECT COUNT(*) AS total_orders
FROM [Tibi Food Dataset]
WHERE DATEPART(QUARTER, order_create_date) = 4 -- For Q4 2023

SELECT 
    DATEPART(QUARTER, order_create_date) AS Quarter,
    Count(order_create_date) AS NumberofOrderbyQuarter
FROM 
    [Tibi Food Dataset]
GROUP BY 
    DATEPART(QUARTER, order_create_date)
ORDER BY 
    Quarter;

SELECT SUM(Order_Total_Gross) AS gmvQ3
FROM
   [Tibi Food Dataset]
WHERE DATEPART(QUARTER, order_create_date) = 3 -- For Q3 2023

SELECT SUM(Order_Total_Gross) AS gmvQ4
FROM
   [Tibi Food Dataset]
WHERE DATEPART(QUARTER, order_create_date) = 4 -- For Q4 2023

SELECT SUM(Order_Total_Gross) AS gmvQ2
FROM
   [Tibi Food Dataset]
WHERE DATEPART(QUARTER, order_create_date) = 2 -- For Q4 2023

SELECT 
    (SUM(CASE WHEN finished_order_status ='success' THEN 0 ELSE 1 END) / COUNT(*)) * 100 AS successful_delivery_percentage
FROM
    [Tibi Food Dataset]
WHERE DATEPART(QUARTER, order_create_date) = 3 -- For Q3 2023

SELECT 
    (SUM(CASE WHEN finished_order_status = 'success' THEN sum 1 Then 0 END) / COUNT(*)) * 100 AS successful_delivery_percentage,
    (SUM(CASE WHEN finished_order_status = 'rejected' THEN sum 1 Then 0 END) / COUNT(*)) * 100 AS rejected_delivery_percentage
FROM
   [Tibi Food Dataset]
WHERE DATEPART(QUARTER, order_create_date) = 3 -- For Q3 2023

SELECT 
    (SUM(CASE WHEN finished_order_status = 'success' THEN 1 ELSE 0 END) / COUNT(*)) * 100 AS success_percentage
FROM
     [Tibi Food Dataset];
```



### Conclusion
Through this project, we aim to provide Tibi Foods with actionable insights to optimize their operations and drive revenue growth. By leveraging data-driven decision-making, Tibi Foods can enhance customer satisfaction, streamline processes, and achieve sustainable business success.

