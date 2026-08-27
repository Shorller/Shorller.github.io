---
layout: page
title: Sales & Customer Demography Dashboard
description: Interactive Power BI analysis of sales performance, profitability and customer demographics
img: assets/img/10alytics-sales-cover.png
importance: 5
category: analytics
---

<div class="mb-4">
  <a href="{{ '/projects/' | relative_url }}">← Back to projects</a>
</div>

I developed a two-page **Power BI dashboard** to analyse company sales performance, profitability and customer demographics. The project focused on transforming transactional data into an interactive reporting tool that allows users to move between an executive sales overview and a more detailed customer-demography analysis.

### Sales performance

The Sales view tracks key performance indicators including total sales, profit, profit margin and order volume, alongside trends by product category, region and time.

Key findings included:

- **£470.53K in total sales** and **£61.62K in profit**, producing a **13.10% profit margin**
- Approximately **2,000 orders** across the dataset
- **Furniture generated the highest category sales** at approximately £170K, narrowly ahead of Technology and Office Supplies
- The **East region** recorded the strongest sales performance
- Monthly sales showed substantial variation, including a strong increase between June and September and another rise toward the end of the year

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/10alytics-sales-view.png" title="Sales performance dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Sales overview showing KPIs, category and regional performance, top products and monthly trends.
</div>

### Customer & profitability analysis

The second dashboard page explores customer segments, shipping preferences, geographic performance and profitability.

The analysis showed:

- **573 customers**, averaging approximately **£821 in sales per customer**
- The **Corporate segment generated the largest share of profit**, contributing more than 47%
- **Standard Class** was the dominant shipping preference, representing approximately 62% of orders
- California generated the highest overall sales, while geographic analysis highlighted differences between sales volume and profitability across states

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/10alytics-demography-view.png" title="Customer demography dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Customer and profitability view showing segment performance, shipping preferences, leading customers and geographic patterns.
</div>

### Dashboard development

I used **Power BI and DAX** to develop calculated measures and KPIs, create interactive visualisations and organise the analysis into two connected reporting views.

The dashboard includes:

- KPI cards for sales, profit, margin and orders
- Time-series analysis
- Product and category comparisons
- Regional and state-level analysis
- Customer-segment analysis
- Interactive filtering and report navigation

### Tools

`Power BI` `DAX` `Data Visualisation` `Business Intelligence`

_10Alytics Power BI training project._

<div class="mb-4">
  <a href="{{ '/projects/' | relative_url }}">← Back to projects</a>
</div>
