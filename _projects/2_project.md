---
layout: page
title: Hotel Haven
description: Predicting hotel booking cancellations with Random Forest
img: assets/img/hotel-haven-cover.png
importance: 2
category: machine-learning
---

Hotel Haven, a luxury hotel chain, was struggling with high cancellation rates - leading to lost revenue, unfilled rooms, and disrupted staffing and resource planning. This project builds a predictive model to flag high-risk bookings before they cancel, so the hotel can act ahead of time rather than reactively.

### The problem

The existing system gave no insight into *why* customers were cancelling, and no way to identify high-risk bookings in advance. Hotel Haven wanted to better understand booking patterns and reduce cancellations without a clear, data-driven way to do it.

### Approach

- **Data cleaning**: Worked with 36,285 bookings across 17 original features. Capped invalid binary anomalies, removed 37 rows with an impossible date (29 Feb 2018, not a leap year), and confirmed no missing values or duplicates
- **EDA**: Explored univariate and bivariate patterns - lead time, price, special requests, booking channel, and room type all showed clear relationships with cancellation
- **Feature engineering**: Expanded to 25 features, including lead time buckets, price-per-night, weekend/stay-structure flags, and guest commitment indicators; dropped features with severe multicollinearity (0.93 correlation)
- **Modelling**: Compared Logistic Regression, Decision Tree, Random Forest, and XGBoost on an 80/20 stratified split; selected and tuned **Random Forest** as the best performer across all three evaluation metrics

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/hotel-haven-confusion-matrix.png" title="Confusion matrix" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Confusion matrix for the tuned Random Forest model on the held-out test set.
</div>

### Results

- **Accuracy: 90.21%** · **ROC-AUC: 95.39%** · **F1 Score: 90%**
- **Lead time was the strongest predictor** - cancelled bookings had a median lead time of 122 days vs 39 days for completed bookings, and lead-time features alone accounted for over 31% of the model's decisions
- **Special requests strongly reduced cancellation risk** - dropping from 43.2% with no requests to 0% with 3 or more
- **Booking channel mattered** - Online bookings cancelled at 36.5% vs just 10.9% for Corporate

### Recommendations delivered

- Flag bookings made 90+ days in advance as high risk for proactive retention outreach
- Prompt guests to add special requests at booking - even one request roughly halves cancellation likelihood
- Apply stricter deposit policies for Online bookings and long lead-time reservations
- Plan for a seasonal cancellation peak (April–October, especially July at 45%)
- Investigate Room Type 6, which cancelled at 42.1% - well above other room types

### Tools

`Python` `pandas` `scikit-learn` `Random Forest` `XGBoost` `Logistic Regression`

### Links

- **Full presentation**: [Download PDF](/assets/pdf/Hotel_Haven_Presentation_Oluwashola.pdf)

---
*10Alytics Machine Learning Capstone Project*
