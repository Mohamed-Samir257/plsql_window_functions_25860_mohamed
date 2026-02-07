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

### ER Diagram 
```mermaid
erDiagram
  REGIONS ||--o{ CUSTOMERS : has
  REGIONS ||--o{ PRODUCTS : stocks
  CUSTOMERS ||--o{ ORDERS : places
  ORDERS ||--o{ ORDER_ITEMS : contains
  PRODUCTS ||--o{ ORDER_ITEMS : sold_as
