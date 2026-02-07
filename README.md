# INSY 8311 — SQL Assignment I (JOINs + Window Functions)
**Student:** Mohamed Samir Abdelmotalab  
**Student ID:** 25860
**Group:** A
**Repo:**  plsql_window_functions_25860_mohamed

-

## 1) Business Problem (Context + Challenge)
KigaliMart Ltd is a retail company selling products across Rwanda. The Sales & Operations team needs better reporting to understand performance per region and improve decisions on inventory and marketing.

**Problem:** Management cannot easily identify top-selling products, high-value customers, regional growth trends, and inactive customers/products with no sales.  
**Goal:** Use SQL JOINs and Window Functions to generate actionable reports.

**Expected Outcome:**
Produce SQL reports that rank top products/customers per region, compute running totals and moving averages, measure month-over-month growth, and segment customers into quartiles for targeted actions.
-

## 2) Success Criteria 
1. Rank Top 5 products per region by revenue (RANK).
2. Compute running monthly revenue per region (SUM OVER).
3. Compute month-over-month growth (LAG/LEAD).
4. Segment customers into spend quartiles (NTILE(4)).
5. Compute 3-month moving average per region (AVG OVER).

## 3) Database Schema 
### Tables
- `regions(region_id PK)`
- `customers(customer_id PK, region_id FK)`
- `products(product_id PK, region_id FK)`
- `orders(order_id PK, customer_id FK)`
- `order_items(order_item_id PK, order_id FK, product_id FK)`
## 4) Results Analysis
**Descriptive**
Sales performance differs by region, with some regions generating higher total revenue than others.
A small number of products contribute to a large share of sales, and the ranking results show clear “top sellers” per region.
Monthly totals show ups and downs over time, while the moving average highlights the overall trend more clearly.

**Diagnostic **
Regions with higher revenue usually have more active customers and more frequent orders (higher order volume).
Some regions perform lower because there are inactive customers (customers with no orders) or low demand for certain products.
Products with no sales suggest issues like wrong pricing, low visibility, poor regional fit, or overstocking in the wrong locations.

**Prescriptive**
Run promotions for inactive customers (welcome discounts, SMS/WhatsApp reminders, loyalty offers).
For products with no sales, apply discounts, bundles, or remove/replace them based on category performance.
Increase stock and marketing focus on top products per region, and reduce stock in regions where demand is low.
Use the month-to-month growth report to repeat successful campaigns in months that showed strong growth and investigate drops quickly.

### References
References
  Oracle Analytic Functions (Window Functions) Documentation:
https://docs.oracle.com/en/database/oracle/oracle-database/

PostgreSQL Window Functions Documentation:
https://www.postgresql.org/docs/current/tutorial-window.html

dbdiagram.io (ERD tool):
https://dbdiagram.io/

### ER Diagram 
```mermaid
erDiagram
  REGIONS ||--o{ CUSTOMERS : has
  REGIONS ||--o{ PRODUCTS : stocks
  CUSTOMERS ||--o{ ORDERS : places
  ORDERS ||--o{ ORDER_ITEMS : contains
  PRODUCTS ||--o{ ORDER_ITEMS : sold_as




