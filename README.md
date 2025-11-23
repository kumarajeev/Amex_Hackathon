# 🏦 Amex Campus Challenge 2025 – Offer Personalization

This repository contains the complete solution for the **American Express Campus Challenge 2025**. The task was to build a predictive model that ranks offers shown to customers, estimating the probability that they will click on an offer once it is shown.

> 📎 Kaggle Notebook: [View Solution](https://www.kaggle.com/code/rudrakshkawde/main-amex-main)  
> 📁 Dataset Folder: [Download Data](https://drive.google.com/drive/folders/1c9jFRR5eWorz6JbXQ5RQIa9uFk5o7_lD?usp=sharing)

---

## 🧠 Problem Statement

Given a customer, an offer, and a placement date — predict the **probability of click** conditional on impression (`P(click | impression)`). The goal is to **rank relevant offers higher** to increase customer engagement.

- Evaluation Metric: **MAP@7 (Mean Average Precision at 7)**
- Final submission requires predicting **top 7 ranked offers** for each customer per day.

---

## 🛠️ Key Techniques Used

- LightGBM ranking model (`lambdarank` objective)
- Extensive categorical encoding & feature engineering
- Session-level aggregation from transactions and events
- Click-through-rate and offer-level statistics
- Temporal features from timestamps
- Merging external data for customer, offer, and impression enrichment

---

## 📊 Data Files Overview

| File Name                | Description                                    |
|-------------------------|------------------------------------------------|
| `train_data.parquet`    | Click labels + impressions for training        |
| `test_data.parquet`     | Test set to predict offer ranks on             |
| `add_event.parquet`     | Impression/click timestamp logs                |
| `add_trans.parquet`     | Customer-level transaction history             |
| `offer_metadata.parquet`| Metadata about each offer                      |
| `data_dictionary.csv`   | Description of anonymized features             |

---

## 📈 Evaluation Metric

> **MAP@7**: Measures average precision per customer, weighted by the rank of true positive clicks.

This encourages models to push the highest-click-probability offers to the top 7 positions.
