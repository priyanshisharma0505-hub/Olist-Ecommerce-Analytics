# Olist E-Commerce Analytics Portfolio

## What is this project?
I built this dashboard to analyze the real-world Olist Brazilian e-commerce dataset. My main goal was to go beyond just dragging and dropping charts in Power BI. I wanted to explore the raw relational data in PostgreSQL first, validate my metrics, and then build an interactive visualization layer that accurately reflects those numbers.

## Tools I Used
* **PostgreSQL:** For initial data exploration, testing joins, and establishing baseline metrics.
* **Power BI & DAX:** For building the dashboard, connecting tables, and calculating measures.

## Key Findings
* **Total Volume:** I analyzed a validated dataset of 99,441 completed orders.
* **Revenue Drivers:** Credit cards dominate the payment methods (driving over R$ 10M in revenue). The top-selling product categories are Health & Beauty, Watches & Gifts, and Bed Bath & Table.
* **Delivery Impact:** The overall on-time delivery rate is strong at 90.45%. I found that when an order is late, the average customer review score drops significantly compared to on-time deliveries.

## Investigating a DAX vs. SQL Engine Discrepancy
The most interesting part of this project was dealing with how different tools calculate averages. 

During my initial SQL validation, I calculated the average review score for "Late" deliveries to be **2.39** (by grouping unique orders first). But when I built the initial DAX measure in Power BI, it returned **2.27**. 

Instead of ignoring the mismatch, I investigated the root cause. I realized Power BI's active data model relationships and handling of blank review rows process data differently than a raw SQL `LEFT JOIN`. By rewriting the DAX using `AVERAGEX` and explicitly filtering out empty review rows, I brought the metric to **2.28**. I chose to document this variance rather than force a match to highlight how different BI engines process data under the hood.

## Dashboard Screenshots

### 1. Business Overview
<img width="708" height="591" alt="Page1" src="https://github.com/user-attachments/assets/c2864344-617b-459c-9d78-469b77c27256" />

### 2. Delivery & Customer Satisfaction
<img width="746" height="588" alt="Page2" src="https://github.com/user-attachments/assets/a294c98a-c075-4fed-b544-2f47a0432ee2" />

### 3. Product & Payment Analysis
<img width="1200" height="450" alt="Page3" src="https://github.com/user-attachments/assets/e75b2352-4e9e-4d5b-8abd-35e438836e63" />


