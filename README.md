# Product-Analytics-Dashboard
This project involves developing a high-level Product Analytics Dashboard that provides actionable insights into key product performance metrics. The dashboard supports strategic decision-making and tracks performance trends effectively.
#
overview
This project involves developing a high-level Product Analytics Dashboard that provides actionable insights into key product performance metrics. The dashboard supports strategic decision-making and tracks performance trends effectively.

# Features 
The dashboard includes the following key visualizations:

- Revenue by Country: Highlights top-performing regions with corresponding revenue.
- Revenue by Date and Year: Displays comparative revenue trends over time.
- Profit and Unit Sales Year-over-Year (YoY) Change: Summarizes YoY growth metrics.
- Revenue Breakdown by Discount Band: Analyzes revenue distribution across different discount categories.
- Detailed Table View: Provides revenue and profit details by country and year.

  Additional Enhancements are included as necessary to provide comprehensive insights
  # GETTING STARTED
  ## Prereusites
  * PPower Bi Desktop: Required to view and interact with the dashboard.
  * Excel: For reviewing the raw data source.
 
  # DATA PREPARATION

  The raw data source was from an Excel and transformed using SQL query. Key steps in data transformation includes
  * Removing duplicates and cleaning null values.
  * Standardizing columns headers for consistency.
    ''' sql
    with cte as (
select
a.Product,
a.category,
a.brand,
a.description,
a.Sale_Price,
a.cost_price,
a.Image_url,
b.date,
b.customer_type,
b.discount_band,
b.country,
b.units_sold,
(Sale_Price*Units_Sold) as Revenue,
(cost_Price*Units_Sold) as Total_cost,
Format (date, 'MMMM') as Month,
Format (date, 'yyyy') as Year
from Product_data a
join product_sales b
on a.Product_ID = b.Product)

Select *,
(1-discount*1.0/100) * Revenue as Discount_revenue
From cte a
join discount_data b
on a.Discount_Band = b.Discount_Band and a.Month =b.Month
'''
### Create the sql view
    ![image alt] ()
    ## Data Import to Power Bi
    I used the Advance Feature, trying to avoid the need for transformation using power Query, This is an Interesting feature and I will recommend it, the steps include:
    * Get Data from SQL server
    * Copy and paste your sql server name and database name in their respective fields
    * Check the advance box options 
    * Copy your sql queries and paste in the sql statement box
    ![image alt] ()
# Visualization
![image at] ()

1) Revenue by Country: Interactive map visualization showing revenue distribution by region.
2) Revenue by Date and Year: Line chart displaying trends over time.
3) Profit and Unit Sales YoY Change: Bar chart summarizing annual growth.
4) Revenue Breakdown by Discount Band: Pie chart or stacked bar chart for discount categories.
5) Detailed Table View: Tabular data for granular insights.

   

