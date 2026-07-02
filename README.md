# Cross-Selling Strategy Optimization — United India Insurance Company (UIIC)
### A Rule-Based, No-ML Analytics Approach

## 📌 Project Overview

United India Insurance Company (UIIC) wants to grow revenue from its existing customer base
through **cross-selling** — offering an additional insurance product to a customer who already
holds one, rather than spending more to acquire brand-new customers.

This project builds a **complete analytics pipeline — data cleaning, exploratory data analysis
(EDA), KPI reporting, and customer segmentation — without using any Machine Learning models**.
Instead, the customer prioritization is driven entirely by **business logic and rule-based
segmentation**, making the solution transparent, explainable, and easy for a non-technical
business team to adopt immediately.

**Dataset:** 50,000 customer records (`Insurance_Data_50k.xlsx`)
**Tech stack:** Python, Pandas, NumPy, Matplotlib, Seaborn (no scikit-learn / no ML)

---

## 🎯 Business Problem

Cross-selling carries less risk than acquiring new customers and increases Customer Lifetime
Value (CLV), but blindly offering a new product to every customer is inefficient. UIIC needed a
way to answer:

1. Who are our customers, and what does the base look like (demographics, income, current
   coverage)?
2. How engaged / "sales-ready" is each customer (based on lead **Rating**: Hot / Warm / Cold)?
3. Which customers should be prioritized first for a cross-sell offer?

### The Three Cross-Selling Scenarios (Business Rules)
For an **existing** customer, a new product offer can result in one of three coverage outcomes:

| Case | Condition | Business Meaning |
|------|-----------|-------------------|
| 1 | New Coverage **>** Current Coverage | Customer is offered an *additional* product on top of an active one — New Coverage = Current + New product coverage |
| 2 | New Coverage **=** Current Coverage | Customer's old policy has expired; new product offered with equal coverage |
| 3 | New Coverage **<** Current Coverage | Customer's old policy has expired; new product offered with a lower coverage |

This framing (from the Business Understanding document) underpins why **Current_Product**,
**Current_Coverage**, and **New_Coverage** are treated as first-class fields throughout the
analysis rather than being dropped or fed into a model.

---

## 🧹 Step 1 — Data Cleaning & Preparation (No ML, Pure Data Engineering)

The raw dataset (50,000 rows × 16 columns) had missing values across nearly every column. Instead
of dropping rows or using generic auto-imputers, a **deliberate, column-specific imputation
strategy** was applied, following the project's Data Engineering Strategy document:

| Technique | Applied To | Logic |
|---|---|---|
| **Simple imputation** (min of mean/median) | `Age`, `Family_Members` | Reduces skew from outliers vs. a plain mean |
| **Mode imputation** | `Education`, `Occupation`, `Job_Title`, `New_Product_Type`, `Rating`, `Gender`, `Marital_Status` | Standard for categorical fields |
| **Group-wise imputation** | `Income` (by `Occupation`), `Current_Coverage` & `New_Coverage` (by product type) | Preserves realistic income/coverage ranges instead of a single global average |
| **Conditional / business-logic imputation** | `Current_Product`, `Current_Product_Type` | If `Current_Product_Type == 'NO'` or `Current_Coverage == 0` → customer has **no product**; otherwise defaults to the most common active product |
| **Target-row drop** | `Converted` | Rows missing the outcome label are removed (can't be used for reporting) |

**Result:** 50,000 → **49,976** clean rows, **0 missing values**, ready for analysis.

Two low-value columns (`Status` — a duplicate of the target, and the free-text detail behind
`Converted`) were dropped to keep the dataset lean.

---

## 📊 Step 2 — Univariate Analysis

Key distributions explored using boxplots, histograms, and count plots:

- **Age:** Median 39, IQR 28–49 → core segment is **working professionals (30–50 yrs)**.
- **Gender:** ~60% Male / 40% Female → possible marketing skew toward male customers.
- **Marital Status:** ~54% Married → strong signal for **family-oriented insurance products**.
- **Education:** Majority are mid-level educated (Bachelor's/Master's) → price-sensitive segment.
- **Rating (lead temperature):** ~48% Cold, ~30% Warm, ~23% Hot → nearly half the base is
  low-engagement and needs re-activation.

## 📈 Step 3 — KPI Dashboard (Business Reporting Layer)

| KPI | Value |
|---|---|
| Total Customers | 49,976 |
| Overall Conversion Rate | **38.18%** |
| Existing Customers | 56.89% |
| New / Prospective Customers | 43.11% |
| Average Customer Age | 38.98 yrs |
| Male Customer Share | 59.80% |

**Takeaway:** A conversion rate of ~38% on a base this size represents a large untapped
opportunity — the goal of the segmentation model below is to concentrate effort on the highest
probability sub-segments.

## 🔍 Step 4 — Bivariate Analysis (Conversion Drivers)

| Comparison | Insight |
|---|---|
| **Rating vs. Conversion** | Hot leads convert best (~39.6%), but the gap vs. Cold (~37.5%) is smaller than expected — Rating alone isn't a strong single predictor |
| **Income vs. Conversion** | Mid-income customers convert better than very low or very high income bands |
| **Age vs. Conversion** | The 30–50 age band shows the strongest conversion propensity |

These findings motivated a **multi-factor rule**, rather than relying on `Rating` alone, to
identify high-value prospects.

---

## 🧩 Step 5 — Rule-Based Customer Segmentation (No ML)

Instead of training a classification model, customers are segmented using **transparent,
auditable business rules** built on top of the cleaned features:

```python
def segment(row):
    if row['Current_Product'] == 'No' and row['Rating'] == 'Hot':
        return 'High Potential'
    elif row['Current_Product'] == 'No':
        return 'Medium Potential'
    else:
        return 'Low Potential'

data['Segment'] = data.apply(segment, axis=1)
```

| Segment | Definition | Conversion Rate |
|---|---|---|
| 🔥 **High Potential** | No current product **and** Hot lead rating | **38.9%** |
| 🟡 **Medium Potential** | No current product, but not yet a Hot lead | 37.6% |
| 🔵 **Low Potential** | Already holds a product (candidate for the 3-case cross-sell logic above) | 38.4% |

**Business Recommendation:**
- **High Potential** customers should be prioritized for immediate outbound sales contact — they
  are actively engaged and have no existing product.
- **Low Potential** (existing product-holders) should be routed through the **cross-selling
  Case 1/2/3 framework** described above rather than a cold acquisition pitch.
- **Medium Potential / Cold-rated** customers are strong candidates for nurture campaigns
  (email/SMS re-engagement) to move them toward "Hot" before a sales call.

---

## 🗂️ Repository Structure

```
├── Insurance_Data_50k.xlsx              # Raw source data
├── Insurance_Data_50k_Cleaned.csv       # Cleaned dataset (output of Step 1)
├── INS_Without_ML.ipynb                 # Full notebook: cleaning → EDA → KPIs → segmentation
├── UIICReportMain.pdf                   # Company/domain background
├── Business_Understanding.pdf           # Cross-selling business rules & CLV concepts
├── Data_Engineering_Strategy.pdf        # Imputation strategy design doc
└── README.md                            # This file
```

---

## ▶️ How to Run

```bash
pip install pandas numpy matplotlib seaborn openpyxl
jupyter notebook INS_Without_ML.ipynb
```

Run all cells top-to-bottom — the notebook is fully self-contained (loads the raw Excel file,
cleans it, produces every chart/KPI above, and outputs the segmented dataset).

---

## 🧠 Why No Machine Learning?

This project intentionally avoids predictive modeling (no logistic regression, no decision
trees, no clustering algorithms) to demonstrate that a well-designed **data engineering +
business-rule** pipeline can already deliver an actionable, explainable segmentation for a
non-technical stakeholder — a natural **baseline** before investing in a more complex ML
solution.

## 🔮 Possible Next Steps (Future Work, Not Implemented Here)

- A supervised classification model (e.g., logistic regression / gradient boosting) to predict
  `Converted` and rank customers by predicted probability.
- Feature importance analysis to validate/refine the current rule-based segments.
- A/B testing the rule-based segments against a model-driven ranking to quantify lift.

---

*Project by [Naresh IT — Data Analyst / Business Analyst Track].*
