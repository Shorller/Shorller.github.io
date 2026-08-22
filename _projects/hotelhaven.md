---
layout: page
title: Hotel Haven
description: Predicting hotel booking cancellations using Random Forest and customer booking patterns
img: assets/img/hotel-haven-cover.png
importance: 3
category: machine-learning
---

I developed a machine learning model to predict hotel booking cancellations and identify the booking characteristics most strongly associated with cancellation risk. The project combined data cleaning, exploratory analysis, feature engineering, model comparison and business recommendations.

The final dataset contained **36,248 bookings**, with approximately one-third ending in cancellation.

### The problem

High cancellation rates can create uncertainty around room availability, staffing and revenue planning. The aim of the project was to determine whether booking information available before arrival could be used to identify reservations with a higher likelihood of cancellation.

The analysis focused on questions such as:

* Does booking lead time affect cancellation risk?
* Are particular booking channels associated with higher cancellation rates?
* Do room type, price and seasonal patterns matter?
* Are guest commitment indicators, such as special requests, associated with lower cancellation rates?

### Data preparation & feature engineering

The original dataset contained **36,285 bookings across 17 features**.

During cleaning and preparation, I:

* Identified and removed **37 records containing an impossible date — 29 February 2018**
* Checked for missing values and duplicates
* Reviewed categorical and numerical distributions for anomalies
* Removed overlapping variables with severe multicollinearity, including features with correlations as high as **0.93**
* Expanded the modelling dataset to **25 engineered features**

Engineered features included:

* Lead-time buckets and log-transformed lead time
* Total nights and long-stay indicators
* Weekend booking and stay indicators
* Price per night and price bands
* Reservation month and day of week
* Special-request indicators
* Repeat-guest indicators

### Exploratory analysis

Several clear patterns emerged before modelling.

* **Lead time showed the strongest relationship with cancellation.** Cancelled bookings had a median lead time of **122 days**, compared with **39 days** for completed bookings.
* **Online bookings had a 36.5% cancellation rate**, compared with **10.9% for Corporate bookings**.
* Bookings with **no special requests cancelled at 43.2%**, compared with 23.8% for bookings with one request and 14.6% for those with two.
* **Room Type 6** had the highest cancellation rate at **42.1%**.
* Cancellation risk also showed a seasonal pattern, with **July recording the highest monthly rate at 45%**.

These patterns were treated as associations rather than evidence that any one factor directly causes cancellation.

### Model development

I compared four classification models using an **80/20 train-test split**:

| Model               |   Accuracy |    ROC-AUC |   F1 Score |
| ------------------- | ---------: | ---------: | ---------: |
| Logistic Regression |     80.81% |     76.56% |     80.44% |
| Decision Tree       |     86.57% |     85.08% |     86.61% |
| Random Forest       | **89.83%** | **87.60%** | **89.74%** |
| XGBoost             |     88.81% |     86.52% |     88.72% |

Random Forest produced the strongest overall performance and was selected for further tuning.

### Final model performance

After tuning, the Random Forest classifier achieved:

* **Accuracy: 90.21%**
* **ROC-AUC: 95.39%**
* **F1 Score: 90%**

On the held-out test set, the model correctly classified **6,540 of 7,250 bookings**.

Its confusion matrix contained:

* **4,600 true negatives** — correctly identified completed bookings
* **1,940 true positives** — correctly identified cancellations
* **273 false positives**
* **437 false negatives**

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/hotel-haven-confusion-matrix.png" title="Random Forest confusion matrix" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Confusion matrix for the tuned Random Forest classifier on the held-out test set.
</div>

### Feature importance

Lead-time features were the strongest contributors to the final model:

* `log_lead_time`: **0.162**
* `lead_time`: **0.153**
* `average_price`: **0.114**
* `price_per_night`: **0.078**
* `reservation_month`: **0.066**
* `market_segment_type`: **0.061**

Lead-time variables alone accounted for more than **31% of total feature importance**, reinforcing the patterns identified during exploratory analysis.

### Business recommendations

Based on the analysis, I recommended that Hotel Haven:

* Prioritise bookings made **90+ days in advance** for additional monitoring or retention activity
* Test targeted reminders or flexible rescheduling options for bookings showing higher-risk characteristics
* Review deposit and cancellation policies for higher-risk booking segments, particularly Online reservations
* Incorporate seasonal cancellation patterns into capacity and revenue planning
* Investigate the unusually high cancellation rate associated with **Room Type 6**
* Explore whether special-request activity can be used as a useful commitment signal, while recognising that the observed relationship does not establish causation

### Limitations

* The model is based on historical booking behaviour and may need retraining as patterns change
* Customer demographics and reasons for cancellation were not available
* Some categories contained relatively small numbers of bookings
* The analysis identifies predictive relationships, not causal effects

### Tools

`Python` `pandas` `NumPy` `scikit-learn` `Random Forest` `XGBoost` `Logistic Regression` `Matplotlib`

### Links

* **Live application:** [Open Streamlit app](https://hotel-haven-cancellation-risk.streamlit.app/)
* **Source code:** [View project on GitHub](https://github.com/Shorller/Hotel-Haven)
* **Project presentation:** [View presentation PDF](/assets/pdf/Hotel_Haven_Presentation_Oluwashola.pdf)

*10Alytics Machine Learning Capstone Project*
