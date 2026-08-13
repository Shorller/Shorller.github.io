---
layout: page
title: Bed Occupancy Forecast Viewer
description: Predictive bed capacity management for Albion Care Network Healthcare
img: assets/img/acn-cover.png
importance: 4
category: analytics
---

A forecasting and alerting system that predicts ward-level bed occupancy 7, 14, and 30 days ahead across 40 wards in 5 hospitals for Albion Care Network — replacing reactive, historical-average-based planning with forward-looking, ward-specific forecasts.

**Live demo:** [acn-project-efrzkuqh3p9gsp56qrmnby.streamlit.app](https://acn-project-efrzkuqh3p9gsp56qrmnby.streamlit.app/)

### The problem

Hospital wards typically respond to bed pressure only after it's already visible, using historical averages that don't reflect what's actually about to happen. The goal was to give each ward a reliable, forward-looking forecast it could act on ahead of time.

### Approach

- Built a full data pipeline across six linked source tables (bed inventory, ED/outpatient arrivals, admissions, staffing, elective surgery), covering over 1.3 million rows
- Each ward automatically selects whichever model - SARIMAX or XGBoost - has tested more accurately on its own recent history
- Built an interactive Streamlit dashboard with per-ward forecast, accuracy, capacity, and trend views, plus a network-wide alerts panel
- Designed four alert types (threshold, relative pressure, admission spikes, forecast drift), with logic to separate chronic from acute pressure and cut false-urgency alerts

### Results

- **Forecast accuracy within 6–11%** on stable, high-occupancy wards such as ICUs
- **Roughly a third fewer false-urgency alerts** after distinguishing chronic from acute capacity pressure
- Confirmed occupancy does **not** predict safe-staffing-ratio breaches, preventing a misleading proxy metric from reaching the dashboard

### Tools

`Python` `pandas` `SARIMAX` `XGBoost` `scikit-learn` `Streamlit` `Plotly` `Power BI`
