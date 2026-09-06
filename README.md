# India E-Commerce Performance Dashboard

A Power BI dashboard analyzing e-commerce sales, customer behavior, and product performance across India, covering the period **June 2024 – June 2026**.

**Tool:** Power BI Desktop · **Records analyzed:** ~250,000 orders across ~40,000 customers

---

## Overview

This report was built to answer core operational and commercial questions for an Indian e-commerce business: where revenue comes from, who the customers are, how they pay and behave, and where the business is exposed to concentration risk. It is organized into four report pages — **Overview**, **Products**, **Customers**, and **Insights** — moving from headline KPIs to segment-level detail to a written analyst summary.

## Dashboard Pages

### 1. Overview
High-level performance snapshot with time and status trends.
- **KPI cards:** Total Revenue (₹ Cr), Total Orders, Average Order Value, Average Delivery Days, Shipping Cost
- **Revenue vs. Discount vs. Quantity** scatter plot — relationship between discounting and order volume/value
- **Order Status** breakdown (donut chart)
- **Revenue/Orders trend by Month** (line chart, with a metric-selector parameter to toggle the plotted measure)
- **Orders by Hour** (line chart) — intraday ordering pattern
- **Orders by Payment Mode** (column chart)
- Slicers: Year, State, Order Status

### 2. Products
Category- and brand-level performance and quality metrics.
- **KPI cards:** Total Revenue (₹ Cr), Return Rate, Cancellation Rate, Success Rate, Top Brand
- **Revenue and Return Rate by Brand** (column charts)
- **Orders by Category** (bar chart)
- **Revenue and Quantity by Product** (bar chart)
- Slicers: Year, Category, Brand, Order Status, State

### 3. Customers
Customer base composition, value, and engagement.
- **KPI cards:** Active Customers, Total Orders, Zero-Order Customers, Average Delivery Days, Total Revenue (₹ Cr)
- **Revenue and Orders by Age Group** (column chart)
- **Customer Tier distribution** by count and by gender (pie charts)
- **Top Customers table** — Customer ID, Name, Tier, Total Orders, Total Revenue
- Slicers: Year, State, Order Status

### 4. Insights
A written, analyst-authored summary of the key findings surfaced by the dashboard (see below) — the "so what" layer on top of the visuals.

## Data Model (inferred schema)

The report's underlying model includes fields consistent with an **Orders fact table** joined to **Customer** and **Product/Category** dimensions, plus a **Date/Calendar** table:

| Entity | Representative Fields |
|---|---|
| Orders | Order_Status, Payment_Mode, Discount_Percent, Shipping_Cost, Quantity, Total_Revenue, Coupon usage, delivery timing |
| Customers | Customer_ID, Customer_Name, Customer_Tier (Platinum/Gold/Silver), Age_Group, Gender, State |
| Products | Product_Name, Category, Brand |
| Calendar | Year, Month, Hour |

Key DAX measures include `Total_Revenue`, `Total_Revenue Cr` (revenue in ₹ Crores), `Total Orders`, `Average Order Value`, `Average Delivery Days`, `Return Rate`, `Successs Rate`, `cancellation_rate`, `Top Brand`, `Active Customers`, and `Zero order Customers`. A what-if parameter (**Metric Selector**) drives the toggle on the Overview trend chart.

## Key Insights

Findings authored on the Insights page of the report:

1. **UPI dominates payment behavior.** UPI accounts for 51.4% of all orders — more than COD, Debit, and Credit Card combined (48.6%), mirroring India's broader digital-payments shift.
2. **Revenue concentrates in the 26–45 age band.** The 26–35 group alone generates ₹256 Cr, and 26–45 combined drive roughly 72% of total revenue; customers 55+ contribute under 6%.
3. **Customer tier distribution looks inverted.** 68% of customers sit in "Platinum," versus 15% Silver and 17% Gold — the opposite of a typical tiering pyramid, flagged here as a possible tier-threshold or logic issue rather than reported at face value.
4. **Coupon adoption is low.** Only 20% of orders (50,185 of 250,000) used a coupon, suggesting a visibility, targeting, or expiry problem if coupons are meant to drive acquisition/retention.
5. **Churn/dormancy is small but non-zero.** 274 of 40,000 customers (0.7%) have never placed an order.
6. **Electronics is a major concentration risk.** Electronics drives 72.6% of total revenue (₹430 Cr of ₹593 Cr), while Books, Beauty, and Grocery combined contribute under 2% — effectively a single-category business, with Home and Sports as the next candidates for diversification.


## Repository Contents

```
Indian_Sales.pbix   # Power BI report (data model + all four pages)
README.md           # This file
```
