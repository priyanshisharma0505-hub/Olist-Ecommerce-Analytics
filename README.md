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
<img width="719" height="609" alt="Page1" src="https://github.com/user-attachments/assets/77f558ac-4a70-4290-a3d6-9e031e2d0c79" />

### 2. Delivery & Customer Satisfaction
<img width="441" height="357" alt="Page2" src="https://github.com/user-attachments/assets/870d0a9e-a6aa-4fb7-bd1f-a19c37cff831" />

### 3. Product & Payment Analysis
<img width="704" height="267" alt="Page3" src="https://github.com/user-attachments/assets/bf4b3d04-8079-44be-b006-6896977514b2" />

