# Bank Marketing Subscription Model
End-to-end machine learning project to predict customer subscription to a term deposit in a CRM marketing context.\
The project focuses on building a **realistic and deployable classification model**, with particular attention to validation strategy, data leakage, and business-driven evaluation.

---

## Project Overview
This project aims to predict whether a customer will subscribe to a term deposit based on historical marketing campaign data from the Bank Marketing Dataset.\
The main objective is not only to maximize predictive performance, but to design a model that can be **used in a real pre-contact marketing scenario**, where only information available *before* contacting the customer can be exploited.

---

## Business Context
In marketing campaigns, contacting uninterested customers generates costs, while missing potential subscribers leads to lost revenue.\
A reliable predictive model can support CRM teams by:
- Prioritizing high-probability customers
- Improving campaign conversion rates
- Reducing unnecessary contact costs
- Supporting data-driven decision making

---

## Key Challenges Addressed
- **Moderate class imbalance**, requiring appropriate evaluation metrics
- **Data leakage risk**, especially due to post-contact variables such as call duration
- **Trade-off between recall and precision**, driven by business considerations
- **Model interpretability**, necessary for stakeholder trust

---

## Methodology

### Exploratory Data Analysis (EDA)
- Analysis of target distribution and feature behavior
- Identification of skewed variables and outliers
- Investigation of relationships between categorical features and subscription behavior

### Validation Strategy
- Train / Validation / Test split with stratification
- Validation set used for model selection and threshold tuning
- Test set reserved for final unbiased evaluation
This strategy ensures a realistic estimate of model performance and avoids optimistic bias.

---

## Modeling Approach
Two main algorithms were evaluated:
- **Logistic Regression** (interpretable baseline)
- **Random Forest** (non-linear model with higher expressive power)
Model selection was based primarily on **ROC-AUC**, while **precision and recall** were used to assess business impact.

---

## Data Leakage Consideration
The feature **call duration** was identified as a source of data leakage, since it is only known after the customer has been contacted.\
For this reason, two scenarios were evaluated:
- A benchmark model including duration (reference only)
- A **realistic deployable model excluding duration**
The final model selection is based exclusively on the leakage-free scenario.

---

## Threshold Optimization
Instead of relying on the default classification threshold (0.5), threshold tuning was performed to improve recall for potential subscribers, reflecting the higher cost of false negatives in marketing campaigns.

---

## Model Interpretability
Model behavior was analyzed using **SHAP (SHapley Additive exPlanations)** to:
- Identify the most influential features
- Understand how customer characteristics drive predictions
- Support trust and transparency in model decisions

---

## Results Summary

- The benchmark model achieves high performance but is not usable in practice due to data leakage
- The realistic model shows moderate but reliable predictive power
- Threshold optimization significantly improves recall, increasing the number of identified potential subscribers

---

## Limitations and Future Work
- Absence of behavioral and transactional time-series data
- Static modeling approach (no model retraining over time)
- Business costs not explicitly quantified in monetary terms
Future improvements could include cost-sensitive learning, profit-based evaluation metrics, and integration with real CRM systems.

---

## Final Remarks
This project demonstrates an end-to-end data science workflow, from data exploration to model interpretation, with a strong emphasis on **real-world applicability and business impact**.

AI tools were used to speed up standard implementation tasks, while project design decisions, validation strategy, and business interpretation were performed manually.
