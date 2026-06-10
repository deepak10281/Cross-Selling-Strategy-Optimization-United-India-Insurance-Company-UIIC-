# Insurance Cross-Selling — Predictive Analytics

> ML-powered cross-selling model for identifying high-potential insurance customers | 89% accuracy | Python · Scikit-learn

---

## Business objective

United India Insurance Company (UIIC) needed to identify which existing customers were most likely to purchase additional insurance products, enabling targeted cross-selling campaigns and reducing acquisition costs.

---

## Model results

| Model | Accuracy | AUC |
|---|---|---|
| Logistic Regression | 88.5% | 0.918 |
| Decision Tree | 88.8% | — |
| **KNN (best)** | **89.15%** | **0.887** |

---

## Key insights

- Customers with higher income showed significantly stronger conversion probability
- "Hot" customer ratings strongly correlated with successful cross-selling
- Customers holding multiple existing policies were most responsive to offers
- VIF-based feature selection (threshold 3.5) removed multicollinearity before modelling

---

## Tech stack

| Tool | Purpose |
|---|---|
| Python (Pandas, NumPy) | Data cleaning & preprocessing |
| Scikit-learn | ML model training & evaluation |
| Matplotlib / Seaborn | EDA visualisation |
| SciPy | Statistical analysis |

---

## Dataset

| Attribute | Detail |
|---|---|
| Records | 100,000 customers |
| Features | 16 |
| Target | Conversion status (converted / not converted) |
| Key fields | Age, income, product type, coverage amount, customer rating |

---

## How to run

```bash
git clone https://github.com/deepak10281/Cross-Selling-Strategy-Optimization-United-India-Insurance-Company-UIIC-.git
pip install pandas numpy scikit-learn matplotlib seaborn
jupyter notebook insurance_cross_selling_analysis.ipynb
```

---

## Future enhancements

- Deploy via Streamlit for real-time prediction
- Hyperparameter tuning with GridSearchCV
- Test XGBoost and LightGBM for accuracy improvement

---

## Author

**Deepak Malviya**  
[LinkedIn](https://www.linkedin.com/in/deepak102825/) · [Email](mailto:deepakmalviya7604@gmail.com)
