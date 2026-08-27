---
layout: page
title: Amazon Reviews Sentiment Analysis
description: End-to-end NLP sentiment classification using fine-tuned DistilBERT
img: assets/img/amazon-sentiment-cover.png
importance: 2
category: nlp
---

<div class="mb-4">
  <a href="{{ '/projects/' | relative_url }}">← Back to projects</a>
</div>

I developed an end-to-end NLP pipeline for classifying customer reviews as **positive, neutral, or negative** using a fine-tuned DistilBERT transformer model. The project takes the analysis from raw review text through model fine-tuning and deployment, with an interactive Streamlit application and Power BI dashboard for exploring wider sentiment patterns.

The project was developed for **ShopEase Europe, a fictional client scenario**, to explore how automated sentiment classification could help turn large volumes of customer feedback into usable business insight.

### The problem

Manually reviewing thousands of customer comments makes it difficult to identify recurring problems, compare sentiment across products, and track patterns at scale.

The project explored how NLP could automate this process while still making the outputs accessible to non-technical users through an interactive application and business-facing dashboard.

### NLP approach

I fine-tuned **DistilBERT** for three-class sentiment classification using cleaned customer review text.

The workflow included:

- Preparing and cleaning review text for modelling
- Tokenising text using the Hugging Face tokenizer
- Fine-tuning DistilBERT for **negative, neutral, and positive** sentiment classification
- Publishing the trained model through Hugging Face
- Building single-review and batch prediction workflows
- Returning sentiment predictions with model confidence scores

For batch analysis, the application accepts CSV files and can classify large collections of reviews, with results available for further analysis and download.

### Model performance

I compared **Naive Bayes, Logistic Regression, and DistilBERT** to assess whether the transformer model improved sentiment classification beyond simpler baselines.

| Model               |   Accuracy | Macro F1 | Weighted F1 |
| ------------------- | ---------: | -------: | ----------: |
| Naive Bayes         |     88.47% |     0.58 |        0.86 |
| Logistic Regression |     89.61% |     0.59 |        0.88 |
| **DistilBERT**      | **90.92%** | **0.69** |    **0.91** |

DistilBERT achieved the strongest overall performance. The most important improvement was on the **Neutral** class: Naive Bayes and Logistic Regression both recorded an F1 score of 0.00 for this minority class, while DistilBERT improved it to **0.23**. Negative and positive reviews were classified much more effectively, with DistilBERT achieving class-level F1 scores of **0.95** and **0.90**, respectively.

The comparison also highlighted the effect of class imbalance. Although overall accuracy was above 88% for all three models, the macro-level metrics revealed substantially weaker performance on the minority Neutral class. This made macro F1, alongside accuracy and weighted F1, important when comparing the models.

### Deployment

I built and deployed an interactive **Streamlit application** so users could test the classifier without interacting directly with the underlying Python code.

The application supports:

- Individual review classification
- Prediction confidence scores
- CSV batch processing
- Sentiment-distribution visualisations
- Product-category comparisons
- Downloadable prediction results

Building the deployment also involved resolving practical engineering issues, including removing large model files from Git history and addressing Streamlit Cloud permissions.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/amazon-sentiment-app.png" title="Streamlit sentiment classifier" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Streamlit interface for individual and batch sentiment classification.
</div>

### Business analysis

Alongside the classifier, I developed a **Power BI dashboard** analysing 20,159 reviews from 2007–2024 across product categories and countries.

Key findings included:

- **70% of reviews were classified as negative**, compared with 26% positive and 4% neutral
- Delivery, refunds and returns were prominent themes within negative feedback
- **Sports** generated high volumes of both positive reviews and delivery/service complaints, indicating high engagement alongside inconsistent customer experiences
- **Home & Living** recorded the lowest average sentiment score at **-0.48**
- The **US and Great Britain** generated the largest overall review volumes, while India and Denmark had comparatively higher proportions of positive sentiment

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/amazon-sentiment-dashboard.png" title="Power BI sentiment dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Power BI dashboard exploring sentiment patterns by category, country and time.
</div>

### Tools

`Python` `Hugging Face Transformers` `DistilBERT` `Streamlit` `Power BI` `Git`

### Links

- **Live application:** [Open Streamlit app](https://amazon-44rsuekqigv6azxzyvsmbe.streamlit.app/)
- **Source code:** [View project on GitHub](https://github.com/Shorller/Amazon)
- **Power BI dashboard:** [View dashboard PDF](/assets/pdf/Amazon_Sentiment_Analysis.pdf)

<div class="mb-4">
  <a href="{{ '/projects/' | relative_url }}">← Back to projects</a>
</div>
