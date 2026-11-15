# Power BI Data Modeling Project

## Overview
This project turns 23 raw, messy Excel tables into a clean star schema in
Power BI. The source data covers sales orders, customers, products, shipments,
invoices, payments, marketing campaigns, inventory and sales targets. I
followed the Data with Baraa YouTube tutorial and built the model hands-on.

## Data Model
**Fact tables**
- `fact_sales`: order line items (quantity, price, cost, discount, line total)
- `fact_order_process`: order, ship, delivery, invoice and payment dates
- `fact_inventory`: monthly stock units per product
- `fact_campaign_spend`: daily impressions, clicks and spend
- `fact_promotion_coverage`: which products each campaign promoted
- `fact_sales_targets`: monthly revenue targets

**Dimension tables**
- `dim_customer`: customer, segment, account manager, contact and location
- `dim_product`: product, brand, subcategory, category, supplier
- `dim_geo`: city and region (used for ship-to and bill-to cities)
- `dim_order_flags`: order channel, status and priority
- `dim_campaign`: campaign name, channel, dates and budget
- `dim_date`: calendar table

**Supporting tables**
- `security`: region-to-user mapping for row-level security
- `_measures`: a dedicated table that holds all DAX measures

**Relationships:** 11 many-to-one relationships with single-direction filtering,
including an inactive relationship so ship-to and bill-to cities can both use `dim_geo`.

## DAX Measures
| Measure | Logic |
|---|---|
| total_sales | Sum of line_total |
| total_orders | Distinct count of order_id |
| total_active_customers | Distinct count of customers who ordered |
| base_total_customers | Count of all customers in dim_customer |
| avg_order_to_pay | Average days from order to payment |

## What I Did
- Cleaned and combined the raw tables in Power Query (for example, merging the 2025 and 2026 order files)
- Designed the star schema with fact and dimension tables
- Created relationships, including a role-playing dimension (`dim_geo`)
- Set up a region-based security table for row-level security
- Wrote DAX measures and organised them in a dedicated measures table
- Built report pages with KPI cards and a customer pivot table

## Tools & Skills
Power BI Desktop, Power Query, DAX, Data Modeling, Star Schema, Excel

## Project Structure
- `report/`: Power BI file (`Data_modeling_project.pbix`)
- `data/`: raw source data (`raw_tables.xlsx`)
- `images/`: screenshots of the data model


## Author
Naga Veera Surya Teja Narina | [LinkedIn](https://www.linkedin.com/in/surya-teja-narina-b4aa5a317/)
