# 🏢 UIIC Cross-Selling Predictive Analysis

## 📘 Overview
This project analyzes customer and policy data from United India Insurance Company (UIIC) to improve cross-selling strategies using predictive analytics and machine learning. The solution focuses on identifying customers who are most likely to purchase additional insurance products by performing data preprocessing, exploratory data analysis (EDA), and predictive model building on a dataset of 100,000 customer records.

---

## 🎯 Objectives
- Analyze customer demographics and policy attributes influencing conversion behavior.
- Identify high-potential customers for cross-selling campaigns.
- Build and compare machine learning models for conversion prediction.
- Recommend the best-performing model for deployment.
- Generate actionable business insights to improve customer retention and revenue growth.

---

## 🧩 Dataset Information
- **Total Records:** 100,000
- **Features:** 16
- **Target Variable:** Conversion Status (Converted / Not Converted)

### Key Features
- Age
- Gender
- Marital Status
- Income
- Education
- Product Type
- Coverage Amount
- Customer Rating
- Existing Policies

---

## ⚙️ Data Preprocessing
The dataset underwent multiple preprocessing and feature engineering steps to improve data quality and model performance.

### Data Cleaning
- Handled missing values using mean, median, and mode imputation.
- Standardized and converted data types.
- Encoded categorical variables for machine learning compatibility.

### Feature Selection
- Removed multicollinearity using Variance Inflation Factor (VIF) analysis.
- Applied a VIF threshold of 3.5 for feature reduction.

---

## 📊 Exploratory Data Analysis (EDA)
Performed extensive EDA to uncover trends, patterns, and customer behaviors affecting cross-selling conversions.

### Analysis Conducted
- Demographic analysis by age, gender, and marital status.
- Income and coverage analysis across customer groups.
- Product-wise conversion trends.
- Customer rating and conversion relationship analysis.

### Visualizations Used
- Bar Charts
- Histograms
- Heatmaps
- Correlation Matrix
- Box Plots
- Count Plots

---

## 🤖 Machine Learning Models
Three classification models were trained and evaluated to predict customer conversion probability.

| Model | Accuracy | AUC Score |
|-------|-----------|------------|
| Logistic Regression | 88.5% | 0.918 |
| Decision Tree | 88.8% | — |
| K-Nearest Neighbors (KNN) | **89.15%** | 0.887 |

### ✅ Best Performing Model
**K-Nearest Neighbors (KNN)** achieved the highest prediction accuracy and delivered strong classification performance for identifying customers likely to purchase additional insurance products.

---

## 🧠 Key Insights
- Customers with higher income levels showed stronger conversion probability.
- “Hot” customer ratings strongly correlated with successful cross-selling.
- Customers with multiple insurance products were more responsive to offers.
- Higher coverage-value customers demonstrated increased engagement.
- Balanced demographic targeting improved campaign effectiveness.

---

## 🛠️ Tech Stack

### Languages
- Python
- R

### Libraries & Frameworks
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn

### Tools
- Jupyter Notebook
- RStudio

---

## 📈 Results
- Achieved approximately **89% prediction accuracy** using the KNN model.
- Identified optimal customer segments for targeted cross-selling campaigns.
- Enabled data-driven recommendations for improving customer retention and revenue growth.

---

## 📁 Repository Structure

UIIC-CrossSelling-Analysis/
│
├── data/                # Raw and cleaned datasets
├── notebooks/           # EDA and machine learning notebooks
├── visuals/             # Charts and visualizations
├── report/              # Final PDF report
├── models/              # Saved ML models
└── README.md            # Project documentation

---

## 🚀 Future Enhancements
- Deploy the model using Flask or Streamlit.
- Implement real-time prediction APIs.
- Perform hyperparameter tuning for improved accuracy.
- Explore advanced models such as Random Forest, XGBoost, and LightGBM.

---

## 👨‍💻 Author
**Deepak Malviya**  
📧 Email: Deepakmalviya7604@gmail.com  
💼 LinkedIn: linkedin.com/in/deepak102825

---

## ⭐ Conclusion
This project demonstrates how predictive analytics and machine learning can enhance insurance cross-selling strategies by identifying high-potential customers, improving campaign targeting, and supporting data-driven business decisions.
