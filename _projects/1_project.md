---
layout: page
title: NutriGlyc AI
description: Predicting post-meal glucose spikes with XGBoost and explainable AI
img: assets/img/nutriglyc-cover.png
importance: 1
category: machine-learning
---

Post-meal glucose spikes are a key early indicator of metabolic risk, but most people have no way to predict them before eating. **NutriGlyc AI** is a machine learning pipeline that predicts glucose spike likelihood from meal and lifestyle data, giving users an early warning before symptoms appear.

### The problem

Existing glucose monitoring is reactive - it tells you what already happened, not what's about to. The goal was to build a model that flags high-risk meals *before* consumption, using data that's realistically available (meal composition, timing, recent activity).

### Approach

- **Data cleaning & EDA**: Cleaned a multi-week glucose monitoring dataset, handled missing sensor readings, and explored spike patterns against meal timing and macronutrient balance
- **Modelling**: Trained an XGBoost classifier, tuned via `RandomizedSearchCV` across learning rate, max depth, and subsample ratios
- **Explainability**: Applied SHAP analysis to identify which features drove individual predictions — critical for a health tool where "black box" outputs aren't good enough
- **Delivery**: Built a Power BI dashboard for non-technical stakeholders, and presented findings in a stakeholder-facing PowerPoint

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/nutriglyc-shap.png" title="SHAP summary plot" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    SHAP summary plot showing which features most influenced glucose spike predictions.
</div>

### Results

- **Recall: 0.83** - the model catches the large majority of true spike events, which matters most for a health-risk tool where missed spikes are costlier than false alarms
- **ROC-AUC: 0.85** - strong overall separation between spike and non-spike cases across thresholds

### Tools

`Python` `XGBoost` `SHAP` `RandomizedSearchCV` `Power BI`

---
*Part of the Data Science Internship programme with Amdari.io / 10Alytics.*
