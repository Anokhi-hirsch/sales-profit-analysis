## Project : Sales Data Analysis performed on Power BI & MySQL

### Project Overview

- Analyzed sales data for a computer hardware and peripheral manufacturer.
- Developed ETL mappings using MySQL, extract the data from unstructured data, transformed it to the staging area, conducted data cleaning and design star schema data model on Power BI.
- Created Power BI dashboards to perform sales and profit analysis, produced quantitative visualizations to draw valuable insights based on different parameters affecting the company performance and provided business solutions.

### Key Technologies used
- Power BI
- MySQL

### About the Dataset
The data includes order information, sales details, customer data, and shipping information.

Download file: <code>[sales_data.sql](https://github.com/Anokhi-hirsch/sales-data-analysis/blob/main/sales_data.sql)</code>

### Data Cleaning & Transformation

Some of the key steps in data cleaning included:
- **Currency Conversion:** Converted sales amounts in USD to INR.
- **Negative Sales Amounts:** Filtered out negative entries in the sales amount column.
- **Currency Duplication:** Standardized duplicated currency values.

### Exploratory Data Analysis Using SQL
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

### Data Modeling

The data model was created using a star schema with a central fact table (sales transactions) connected to dimension tables (customers, products, markets, etc.) as following.

<img width="60%" src="https://github.com/Anokhi-hirsch/sales-data-analysis/blob/main/dashboard-images/star-schema.jpg" />

### Power BI Dashboard
An interactive dashboard was created in Power BI to visualize the following:

<img width="60%" src="https://github.com/Anokhi-hirsch/sales-data-analysis/blob/main/dashboard-images//initial-sales-analysis.jpg" />
</p>

For example, we can see by selection, in year 2020, revenue in Delhi region what 77.73 million, where it dramatically decreased by June 2020 according to revenue trend.

<img width="60%" src="https://github.com/Anokhi-hirsch/sales-data-analysis/blob/main/dashboard-images/interactive-1.jpg" />
</p>


