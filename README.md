# Insurance Cross-Selling — Predictive Analytics

> Identifying high-potential customers for cross-selling using ML | **89% accuracy** with KNN on 100,000 records | Python · Scikit-learn

[![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat-square&logo=python)](https://python.org)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?style=flat-square&logo=scikit-learn)](https://scikit-learn.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat-square&logo=jupyter)](https://jupyter.org)

---

## Business objective

United India Insurance Company (UIIC) needed to identify which existing customers were most likely to purchase additional insurance products — enabling targeted campaigns, reducing acquisition cost, and growing revenue per customer.

---

## Model comparison

| Model | Accuracy | AUC Score |
|---|---|---|
| Logistic Regression | 88.5% | 0.918 |
| Decision Tree | 88.8% | — |
| **KNN (selected)** | **89.15%** | **0.887** |

KNN selected as the production model based on highest classification accuracy.

---

## Key insights

- Customers with **higher income** showed significantly stronger conversion probability
- **"Hot" customer rating** was the single strongest predictor of cross-sell success
- Customers holding **multiple existing policies** were most responsive to new product offers
- **VIF-based feature selection** (threshold 3.5) removed multicollinearity and improved model stability
- Balanced demographic targeting across age and gender improved overall campaign effectiveness

---

## Dataset

| Attribute | Detail |
|---|---|
| Records | 100,000 customers |
| Features | 16 |
| Target variable | Conversion status (Converted / Not Converted) |
| Key fields | Age, gender, marital status, income, product type, coverage amount, customer rating, existing policies |

---

## Data preprocessing steps

- Missing value imputation using mean, median, and mode
- Categorical variable encoding for ML compatibility
- Multicollinearity removal using Variance Inflation Factor (VIF) analysis at threshold 3.5
- Data type standardisation and feature scaling

---

## EDA highlights

- Demographic analysis: age, gender, marital status vs conversion rate
- Income and coverage amount distribution across customer segments
- Product-wise conversion trend analysis
- Correlation heatmap and feature importance ranking

Visualisations used: bar charts, histograms, heatmaps, box plots, count plots, correlation matrix

---

## Tech stack

| Tool | Purpose |
|---|---|
| Python (Pandas, NumPy) | Data cleaning & feature engineering |
| Scikit-learn | Model training, evaluation, VIF analysis |
| Matplotlib / Seaborn | EDA visualisation |
| Jupyter Notebook | Analysis workflow |

---

## Project structure

```
insurance-cross-selling-ml/
│
├── insurance_cross_selling_eda.ipynb        ← EDA & data cleaning
├── insurance_cross_selling_with_ml.ipynb    ← ML models & evaluation
├── insurance_eda_report.html                ← EDA HTML report
├── Insurance_Data_50k.xlsx                  ← Raw dataset
├── cleaned_Insurance_data_50k.csv           ← Cleaned dataset
├── UIIC-Report(Main).pdf                    ← Full project report
└── README.md
```

---

## How to run

```bash
git clone https://github.com/deepak10281/Cross-Selling-Strategy-Optimization-United-India-Insurance-Company-UIIC-.git
cd Cross-Selling-Strategy-Optimization-United-India-Insurance-Company-UIIC-
pip install pandas numpy scikit-learn matplotlib seaborn
jupyter notebook insurance_cross_selling_with_ml.ipynb
```

---

## Results

- **89% prediction accuracy** using KNN on 100,000 customer records
- Identified top customer segments for targeted cross-selling campaigns
- Generated actionable business rules for marketing and retention teams
- VIF analysis reduced feature set from 16 → optimal subset, improving model reliability

---

## Future enhancements

- Deploy model via Streamlit for real-time customer scoring
- Hyperparameter tuning with GridSearchCV
- Test Random Forest, XGBoost, LightGBM for accuracy improvement
- Build customer scoring API for CRM integration

---

## Author

**Deepak Malviya**
[LinkedIn](https://www.linkedin.com/in/deepak102825/) · [Email](mailto:deepakmalviya7604@gmail.com) · [GitHub](https://github.com/deepak10281)
