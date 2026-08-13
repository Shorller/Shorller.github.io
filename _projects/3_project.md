---
layout: page
title: ShopEase
description: End-to-end NLP sentiment classification with DistilBERT
img: assets/img/amazon-sentiment-cover.png
importance: 3
category: nlp
---

Understanding customer sentiment at scale is a core challenge for any e-commerce business. This project delivers an **end-to-end NLP pipeline** that classifies Amazon product reviews by sentiment, built for a fictional client, ShopEase Europe, and deployed as a live interactive demo.

### The problem

Manually reading through thousands of reviews to gauge customer sentiment doesn't scale. ShopEase Europe needed an automated way to classify reviews as positive or negative, so the team could quickly spot problem products and shifting customer sentiment.

### Approach

- **Model**: Fine-tuned **DistilBERT**, a lightweight transformer model, for binary sentiment classification on review text
- **Pipeline**: Built the full workflow from raw text preprocessing through tokenisation, fine-tuning, and evaluation
- **Deployment**: Published the trained model to Hugging Face and built a live **Streamlit** demo so non-technical stakeholders could test it directly
- **Engineering**: Worked through real deployment challenges, including rewriting git history to remove large model files from version control and resolving Streamlit Cloud permissions issues

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/amazon-sentiment-app.png" title="Streamlit demo interface" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Live Streamlit demo interface for the sentiment classifier.
</div>

### Links

- **GitHub**: [Shorller/Amazon](https://github.com/Shorller/Amazon)
- **Model**: [shorller/distilbert-sentiment](https://huggingface.co/shorller/distilbert-sentiment) on Hugging Face

### Tools

`Python` `Hugging Face Transformers` `DistilBERT` `Streamlit` `Git`
