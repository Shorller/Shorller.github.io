---

layout: page
title: Hospital Bed Occupancy Forecasting & Capacity Management
description: Ward-level bed occupancy forecasting, capacity alerts, and model monitoring using SARIMAX and XGBoost
img: assets/img/acn-cover.png
importance: 1
category: analytics
-------------------

I developed an end-to-end forecasting and alerting system to predict ward-level bed occupancy 7, 14, and 30 days ahead across 40 wards in five hospitals. The system combines ward-specific forecasting with capacity alerts and model monitoring, providing a forward-looking alternative to planning based primarily on historical averages.

*Albion Care Network (ACN) is a simulated healthcare network and the project uses synthetic data developed for this data science project.*

**Live demo:** [Explore the Streamlit application](https://acn-project-efrzkuqh3p9gsp56qrmnby.streamlit.app/)

### The problem

Bed demand can vary considerably across wards and over time. Relying on historical averages or responding only when capacity pressure is already visible can make it difficult to anticipate emerging demand.

The project explored how forecasting could provide earlier, ward-specific insight into expected occupancy while also distinguishing between persistent capacity pressure and unusual short-term changes.

### Data

The analysis brought together six linked source tables covering bed inventory and occupancy, ED and outpatient activity, admissions and discharges, staffing and resources, and elective surgery.

Overall, the project covered:

* **40 wards across five hospitals**
* **Six linked source tables**
* **More than 1.3 million records**
* Ward-level occupancy, admissions, arrivals, staffing, capacity and elective activity

This required combining data from different operational areas into a consistent structure suitable for forecasting and monitoring.

### Forecasting approach

Rather than applying one forecasting model across the entire network, I developed a ward-level approach using **SARIMAX and XGBoost**.

* Prepared and validated time-series data for each ward
* Trained SARIMAX and XGBoost forecasting models
* Evaluated model performance against recent observed occupancy
* Selected the better-performing model for individual wards and forecast horizons
* Generated forecasts 7, 14 and 30 days ahead
* Reconciled forecasts with actual occupancy to monitor performance over time

This approach allowed model selection to reflect differences in occupancy patterns between wards rather than assuming that a single modelling method would perform best everywhere.

### Dashboard, alerts & monitoring

I built an interactive **Streamlit application** to turn the forecasting pipeline into a usable decision-support tool.

The application provides ward-level views of:

* Forecast occupancy and capacity pressure
* Historical and recent occupancy trends
* Forecast accuracy and backtesting
* Staffing and capacity information
* Model performance and forecast drift

I also developed a network-wide alerting system covering threshold pressure, relative capacity pressure, admission spikes and forecast drift.

The alert logic distinguishes between **chronic pressure** and **acute changes**, helping prevent wards that routinely operate at high occupancy from continuously generating the same level of urgency.

### Results

* Forecasts on stable, high-occupancy wards such as ICUs achieved errors of approximately **6–11%**
* Distinguishing chronic from acute capacity pressure reduced false-urgency alerts by roughly **one-third** during initial testing
* Analysis showed that occupancy alone did **not** reliably predict safe-staffing-ratio breaches, so it was not used as a proxy for staffing risk in the dashboard
* Ward-specific model selection allowed the system to use whichever forecasting approach performed better for a particular ward and forecast horizon

The project reinforced the importance of evaluating not only whether a model performs well statistically, but also whether the resulting metrics and alerts are meaningful for the decision they are intended to support.

### Tools

`Python` `pandas` `NumPy` `SARIMAX` `XGBoost` `scikit-learn` `Streamlit` `Plotly` `Power BI`

### Links

* **Live application:** [Open Streamlit app](https://acn-project-efrzkuqh3p9gsp56qrmnby.streamlit.app/)
* **Source code:** [View project on GitHub](https://github.com/Shorller/ACN-Project)

