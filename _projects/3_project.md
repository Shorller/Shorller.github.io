---
layout: page
title: Amazon Reviews Sentiment Analysis
description: End-to-end NLP sentiment classification with DistilBERT
img: assets/img/amazon-sentiment-cover.png
importance: 3
category: nlp
---

An end-to-end NLP pipeline that classifies Amazon product reviews by sentiment, built for a fictional client, ShopEase Europe. The project covers the full path from raw review text to a fine-tuned transformer model, a live interactive demo, and a Power BI dashboard translating sentiment patterns into business insight.

**Live demo:** [amazon-44rsuekqigv6azxzyvsmbe.streamlit.app](https://amazon-44rsuekqigv6azxzyvsmbe.streamlit.app/)

### The problem

Manually reading through thousands of reviews to gauge customer sentiment doesn't scale. ShopEase Europe needed an automated way to classify reviews as positive, negative, or neutral, so the team could quickly spot problem products, categories, and shifting sentiment over time.

### Approach

- **Model**: Fine-tuned **DistilBERT**, a lightweight transformer model, for sentiment classification on review text
- **Pipeline**: Built the full workflow from raw text preprocessing through tokenisation, fine-tuning, and evaluation
- **Deployment**: Published the trained model to Hugging Face and built a live **Streamlit** demo so non-technical stakeholders could test it directly
- **Business reporting**: Built a Power BI dashboard analysing 20,159 reviews spanning 2007–2024, across product category and country
- **Engineering**: Worked through real deployment challenges, including rewriting git history to remove large model files from version control and resolving Streamlit Cloud permissions issues

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/amazon-sentiment-app.png" title="Streamlit demo interface" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Live Streamlit demo interface for the sentiment classifier.
</div>

### Key findings

- Across 20,159 reviews, **70% were negative**, 26% positive, and 4% neutral - an overall sentiment score of -0.13
- **Delivery and refunds dominated negative feedback** - "refund," "deliver," "return," and "money" were the top negative keywords, and "money back" and "send back" were among the most common negative bigrams
- **Sports had the highest volume of both delivery and service complaints**, while also containing the most positive reviews - suggesting a high-engagement but inconsistent-experience category
- **Home & Living had the lowest average sentiment score** (-0.48) of any category
- **The US and GB generated the most reviews overall** (positive and negative alike), but **India and Denmark had proportionally the most positive sentiment** relative to their review volume

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/amazon-sentiment-dashboard.png" title="Power BI sentiment dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Power BI dashboard summarising sentiment by category, country, and time.
</div>

### Links
- **PowerBi Dashboards**: [Dashboards](/assets/pdf/Amazon_Sentiment_Analysis.pdf)

### Tools

`Python` `Hugging Face Transformers` `DistilBERT` `Streamlit` `Power BI` `Git`
