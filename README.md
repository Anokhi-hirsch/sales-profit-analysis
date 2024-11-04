# Sales and Profit Analysis Project using Power BI & MySQL

## Project Overview

- Analyzed sales data for a computer hardware and peripheral manufacturer.
- Developed ETL mappings using MySQL, extracted data from unstructured sources, transformed it to the staging area, and conducted data cleaning.
- Designed a star schema data model in Power BI.
- Created Power BI dashboards to perform sales and profit analysis, producing quantitative visualizations to draw valuable insights and provide business solutions.

## Key Technologies used
- Power BI
- MySQL

## About the Dataset
The data includes order information, sales details, customer data, and shipping information.

Download file: <code>[sales_data.sql](https://github.com/Anokhi-hirsch/sales-data-analysis/blob/main/sales_data.sql)</code>

## Data Cleaning & Transformation

Some of the key steps in data cleaning included:
- **Currency Conversion:** Converted sales amounts in USD to INR.
- **Negative Sales Amounts:** Filtered out negative entries in the sales amount column.
- **Currency Duplication:** Standardized duplicated currency values.

## Exploratory Data Analysis Using SQL
Here are some key SQL queries used:

- **Show transactions in US dollars:**
    ```sql
    SELECT * FROM transactions WHERE currency="USD";
    ```
- **Show transactions for the year 2020:**
    ```sql
    SELECT transactions.*, date.* 
    FROM transactions 
    INNER JOIN date ON transactions.order_date=date.date 
    WHERE date.year=2020;
    ```
- **Show total revenue for the year 2020:**
    ```sql
    SELECT SUM(transactions.sales_amount) 
    FROM transactions 
    INNER JOIN date ON transactions.order_date=date.date 
    WHERE date.year=2020 AND (transactions.currency="INR" OR transactions.currency="USD");
    ```
- **Show total revenue for January 2020:**
    ```sql
    SELECT SUM(transactions.sales_amount) 
    FROM transactions 
    INNER JOIN date ON transactions.order_date=date.date 
    WHERE date.year=2020 AND date.month_name="January" AND (transactions.currency="INR" OR transactions.currency="USD");
    ```
- **Show total revenue for the year 2020 in a specific market:**
    ```sql
    SELECT SUM(transactions.sales_amount) 
    FROM transactions 
    INNER JOIN date ON transactions.order_date=date.date 
    WHERE date.year=2020 AND transactions.market_code="Mark001";
    ```

## Data Modeling

The data model was created using a star schema with a central fact table (sales transactions) connected to dimension tables (customers, products, markets, etc.) as following.

<img width="70%" src="https://github.com/Anokhi-hirsch/sales-data-analysis/blob/main/dashboard-images/star-schema.jpg" />

## Power BI Dashboard
An interactive dashboard was created in Power BI to visualize the following:

<img width="70%" src="https://github.com/Anokhi-hirsch/sales-data-analysis/blob/main/dashboard-images//initial-sales-analysis.jpg" />
</p>

For example, we can see by selecting the year 2020, revenue in the Delhi region was 78 million, with a dramatic decrease by June 2020 according to the revenue trend.

<img width="70%" src="https://github.com/Anokhi-hirsch/sales-data-analysis/blob/main/dashboard-images/interactive-1.jpg" />
</p>

Profit Analysis based on feedback from stakeholders.

<img width="70%" src="https://github.com/Anokhi-hirsch/sales-data-analysis/blob/main/dashboard-images/profit-analysis.jpg" />
</p>

## Some Recommendations for Stakeholders
1.	Sales Trend Analysis: Analyze sales data over several years to understand long-term trends and factors affecting sales changes, such as economic conditions and marketing activities.
2.	Monthly Sales Analysis: Regular monthly sales analysis helps understand trends and plan future promotional activities.
3.	Focus on High-Sales Regions: Develop marketing plans and promotional activities tailored to high-sales regions to increase sales effectively.
4.	Product Improvement: Analyze top-ordered products to identify trends in customer needs and improve products accordingly.
5.	Best-Selling Product Focus: Concentrate resources on developing and marketing best-selling products to increase market share.

## Conclusion
This project provided valuable insights into sales performance and customer behavior, enabling data-driven decision-making. By creating an automated dashboard, the sales team can efficiently track sales trends and make informed decisions to boost sales and improve business performance.

## Reference 
This project was inspired by the Sales Insights Data Analysis Project by Codebasics. You can find the original project [here](https://codebasics.io/resources/sales-insights-data-analysis-project).
