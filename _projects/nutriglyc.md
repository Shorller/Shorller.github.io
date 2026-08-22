---
layout: page
title: NutriGlyc AI
description: Glucose spike prediction using tuned XGBoost and SHAP model explainability
img: assets/img/nutriglyc-cover.png
importance: 4
category: machine-learning
--------------------------

I developed a machine learning pipeline to explore whether dietary, clinical and lifestyle information could be used to predict post-meal glucose spike events. The project combined data-quality assessment, feature engineering, model comparison, hyperparameter tuning and SHAP explainability.

The analysis was completed as part of a data science internship project using a structured glucose-spike dataset.

### The problem

The aim was to determine whether information available around meal and patient characteristics could distinguish between spike and non-spike events, while avoiding features that would only become available after the outcome had occurred.

This required answering two questions:

* How accurately could glucose spike events be classified from pre-outcome information?
* Which variables contributed most strongly to the model's predictions?

### Data preparation

The original dataset contained **5,150 records and 28 variables** covering demographic, dietary, clinical and lifestyle characteristics.

Data-quality assessment identified:

* **1,243 missing values** across four variables
* **150 duplicate records**
* Outliers across 16 numerical variables
* No invalid categorical values or numeric-range violations

After removing duplicates, imputing missing numerical values with medians and capping extreme values using IQR-based winsorisation, the cleaned dataset contained:

* **5,000 records**
* **28 variables**
* **No missing values**
* **No duplicate records**

The target remained reasonably balanced, with **2,683 non-spike events (53.7%)** and **2,317 spike events (46.3%)**.

### Preventing data leakage

Exploratory analysis showed that `post_meal_glucose` and `glucose_change` were strongly associated with the target.

However, both variables depend on information available only after the meal outcome, so including them would make the prediction problem unrealistic.

I therefore removed both variables before modelling.

This was an important part of the project because it ensured that model performance reflected information that could plausibly be available before the outcome rather than information derived from it.

### Feature engineering

I created additional features to capture dietary and behavioural patterns, including:

* Carbohydrate and glycaemic-load risk indicators
* Insulin-to-carbohydrate ratio
* Sugar-to-carbohydrate ratio
* Carbohydrate-to-fibre ratio
* Physical-activity and stress indicators
* BMI categories

After feature engineering and target separation, the final modelling dataset contained **32 input features**.

The data was split using an **80/20 stratified train-test split**, with scaling fitted only on the training set to avoid leakage.

### Model comparison

I compared **Logistic Regression, Random Forest and XGBoost**.

| Model               |  Accuracy |     Recall |   F1 Score |    ROC-AUC |
| ------------------- | --------: | ---------: | ---------: | ---------: |
| Logistic Regression |     0.775 |     0.7775 |     0.7619 | **0.8540** |
| Random Forest       |     0.768 |     0.7646 |     0.7532 |     0.8419 |
| **Tuned XGBoost**   | **0.776** | **0.8315** | **0.7746** |     0.8531 |

The tuned XGBoost model achieved the **highest recall and F1 score**, while Logistic Regression produced a marginally higher ROC-AUC.

XGBoost was selected because it identified **385 of 463 spike cases**, reducing false negatives to **78**, compared with 103 for Logistic Regression and 109 for Random Forest.

The model also showed stable cross-validation performance, with a mean ROC-AUC of approximately **0.8445** and a standard deviation of **0.0113**.

### Model explainability

I used **SHAP** to understand which features contributed most strongly to XGBoost predictions.

The leading features by mean absolute SHAP value were:

* **Carbohydrate intake - 32.4%**
* **Insulin-to-carbohydrate ratio - 16.9%**
* **Glycaemic load - 11.7%**
* **Physical activity - 9.4%**
* **Stress level - 5.5%**

The top ten variables accounted for approximately **87.9% of total SHAP importance**.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/nutriglyc-shap.png" title="SHAP feature importance" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    SHAP analysis showing the relative contribution of features to the tuned XGBoost model.
</div>

### Key analytical findings

* Dietary variables, particularly carbohydrate intake and glycaemic load, contributed strongly to model predictions
* The engineered **insulin-to-carbohydrate ratio** became one of the most influential model features
* Physical activity also contributed meaningfully to the model
* Several demographic variables, including age and gender, had relatively low SHAP importance
* Removing post-outcome variables substantially improved the credibility of the prediction setup by preventing target leakage

These findings describe relationships learned from this dataset and should not be interpreted as clinical guidance or causal effects.

### Tools

`Python` `pandas` `NumPy` `scikit-learn` `XGBoost` `SHAP` `RandomizedSearchCV` `Power BI`

### Links

- **Live application:** [Open Streamlit app](https://nutriglyc-glucose-spike.streamlit.app/)
- **Source code:** [View project on GitHub](https://github.com/Shorller/Amdari_P1)

*Data Science Internship project.*
