## Power BI Star Schema Data Modelling

Turned a messy multi-table "nightmare dataset" into a clean, analysis-ready star schema in Power BI.

<img width="1173" height="702" alt="Screenshot 2026-09-22 161820" src="https://github.com/user-attachments/assets/de757060-e7fe-4679-b273-c0a579bbdcc4" />

<img width="1901" height="962" alt="Screenshot 2026-09-29 111055" src="https://github.com/user-attachments/assets/75cf7dfd-fe1d-41d6-8c08-e1f0acc32436" />

## 📌 Project Overview

The raw dataset came as 25+ loosely connected tables with duplicated yearly order tables, unnamed columns, and no date dimension. The goal was to rebuild it as a star schema so reports are fast, DAX is simple, and the numbers can be trusted.

Tools used: Power BI Desktop, Power Query, DAX, [add SQL / Excel if used]

## ❌ The Problem (Before)
Separate order tables per year (ORDERS_2025, ORDERS_2026)
Generic column names (Column1, Column2, ...)
Disconnected tables and ambiguous relationships
Multiple date columns (order, ship, invoice, delivery, pay) with no date dimension
Inconsistent keys across customer, product, and address data

## ✅ The Solution (After)
Combined yearly order tables into a single fact table
Cleaned and renamed columns, fixed data types, and removed duplicates in Power Query
Built dimension tables and a shared date dimension
Used one-to-many relationships with single-direction filtering
Handled role-playing dates using active and inactive relationships with USERELATIONSHIP
Added row-level security and a dedicated measures table

## 🗂️ Data Model
Type	Tables
Fact	fact_sales, fact_order_process, fact_inventory, fact_promotion_coverage, fact_campaign_spend, fact_sales_targets
Dimension	dim_customer, dim_product, dim_campaign, dim_geo, dim_order_flags, dim_date
Other	measures (DAX measures), security (RLS mapping)

## 🔧 Data Cleaning Steps (Power Query)
Combined ORDERS_2025 and ORDERS_2026 using Append Queries
Promoted headers and renamed Column1...n to meaningful names
Fixed data types and standardized date formats
Removed duplicates and handled nulls
Created surrogate keys for [customer / product / geography]

## 🔐 Row-Level Security
Roles: [e.g., Region Manager]
Filter: security[user_email] = USERPRINCIPALNAME()
Effect: each user only sees data for their assigned region

## 💡 Key Learnings
A good model makes DAX simpler and reports faster
Role-playing dimensions need inactive relationships plus USERELATIONSHIP
Fixing data at the source (Power Query) beats patching it in DAX

## 🚀 How to Use
Download the .pbix file from the powerbi/ folder
Open it in Power BI Desktop
Go to Model view to explore the schema

## 👤 Author
Askar Basha R Data Analyst | Power BI · SQL · Tableau · Python · Excel

🔗 LinkedIn : https://www.linkedin.com/in/askarbasha-btech/
