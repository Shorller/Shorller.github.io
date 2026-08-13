---
layout: page
title: Hotel Haven
description: Predicting hotel booking cancellations with Random Forest
img: assets/img/hotel-haven-cover.png
importance: 2
category: machine-learning
---

Hotel booking cancellations create real operational headaches - overbooked or underbooked rooms, wasted marketing spend, and unreliable revenue forecasting. **Hotel Haven** is a classification model that predicts which bookings are likely to be cancelled, giving hotels the chance to intervene early (targeted confirmation emails, flexible rebooking offers, overbooking strategy adjustments).

### The problem

Hotels lose significant revenue to last-minute cancellations, but most reservation systems treat every booking as equally likely to go ahead. Without a way to flag high-risk bookings in advance, hotels can't act until it's too late to recover the lost revenue.

### Approach

- **Data cleaning & EDA**: Explored a hotel bookings dataset covering lead time, deposit type, market segment, and customer history to identify patterns behind cancellations
- **Feature engineering**: Built features capturing booking lead time, prior cancellation history, and deposit/payment behaviour — the strongest early signals of cancellation risk
- **Modelling**: Trained a Random Forest classifier, tuned via `GridSearchCV` across tree depth, estimator count, and minimum leaf samples
- **Delivery**: Packaged findings into a 15-slide stakeholder presentation translating model output into concrete operational recommendations

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/hotel-haven-confusion-matrix.png" title="Confusion matrix" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Confusion matrix showing model performance on the held-out test set.
</div>

### Results

- **Accuracy: 90.21%** - the model correctly classifies the large majority of bookings as cancelled or not
- **AUC: 95.39%** - strong discrimination between the two classes, meaning the model reliably ranks higher-risk bookings above lower-risk ones

### Tools

`Python` `scikit-learn` `Random Forest` `GridSearchCV`

---
*Part of the Data Science Internship programme with Amdari.io / 10Alytics.*
