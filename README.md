# Multi-Table Join Analysis — Brazilian E-Commerce (Olist)

Joins six normalized tables from a real e-commerce dataset into a single analytical
view using both PySpark and Pandas, then visualizes the joined results to answer
business questions that span multiple data sources.

## Business Question
Which product categories generate the most revenue, how does delivery delay affect
review scores, and how does spend vary by payment type and region?

## Dataset
[Brazilian E-Commerce Public Dataset by Olist (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
— 9 relational CSV files covering ~100K orders (orders, items, products, customers,
payments, reviews, geolocation).

## Tools
PySpark (DataFrame joins), Pandas (`merge()`), Seaborn/Matplotlib, Google Colab

## Joins Implemented
| Join | Tables | Type | Why |
|---|---|---|---|
| Orders ↔ Order Items | orders, order_items | INNER | every order must have line items |
| + Products | products | INNER | attach product details |
| + Category Translation | product_category_name_translation | LEFT | some categories lack an English name |
| + Customers | customers | INNER | attach customer location |
| + Payments | payments | LEFT | a few orders lack payment records |
| + Reviews | reviews | LEFT | not every order has a review |

Same join logic was also implemented in Pandas (`merge()`) on a smaller subset of
tables to show the equivalent syntax across both tools.

## Workflow
1. **Clean** each table individually (duplicates, nulls in join keys, date types)
   before joining — joining dirty keys silently drops or duplicates rows
2. **Join** using PySpark across 6 tables into one analytical dataset
3. **Engineer** a delivery delay feature (actual vs. estimated delivery date)
4. **Visualize** the joined result: revenue by category, delivery delay vs review
   score, payment type mix, and regional spend

## Key Findings
*(fill in with your actual results)*
- e.g. [Category] drives the highest revenue despite not having the most orders
- Orders delivered later than estimated show visibly lower review scores
- [Payment type] dominates transaction volume; [state] leads in total revenue

## Repo Structure
