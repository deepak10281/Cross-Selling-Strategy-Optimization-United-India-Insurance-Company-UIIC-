🏢 UIIC Cross-Selling Predictive Analysis
📘 Overview

This project analyzes customer data from United India Insurance Company (UIIC) to improve cross-selling strategies. It involves comprehensive data cleaning, exploratory data analysis (EDA), and machine learning modeling to predict potential customer conversions.

🎯 Objectives

Analyze key customer and policy attributes influencing conversion.

Build predictive models to identify customers likely to purchase additional insurance products.

Compare the performance of multiple models and recommend the best one for deployment.

🧩 Dataset

Records: 100,000

Features: 16 (Age, Gender, Marital Status, Income, Education, Coverage details, etc.)

Target Variable: Conversion Status (Converted / Not Converted)

⚙️ Data Preprocessing

Handled missing values using statistical imputation (mean, median, mode).

Converted and standardized data types.

Removed multicollinearity using VIF threshold (3.5).

Encoded categorical variables for modeling.

📊 Exploratory Data Analysis (EDA)

Demographic distribution by age, gender, and marital status.

Income and coverage analysis by product type.

Conversion trends by product type, rating, and customer profile.

🤖 Model Building

Three models were trained and compared:

Logistic Regression

Decision Tree

K-Nearest Neighbors (KNN)

Model	Accuracy	AUC
Logistic Regression	88.5%	0.918
Decision Tree	88.8%	—
KNN	89.15%	0.887

✅ KNN performed best overall.

🧠 Key Insights

Higher income and strong “Hot” ratings correlate with higher conversion probability.

Customers with higher current coverage and product diversity are more responsive to cross-sell offers.

Balanced demographic targeting can improve cross-selling success.

🛠️ Tech Stack

Languages: Python / R

Libraries: Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn

Tools: Jupyter Notebook, RStudio

📈 Results

Achieved ~89% prediction accuracy using KNN.

Identified optimal cross-selling segments to increase revenue and retention.

📁 Repository Structure
UIIC-CrossSelling-Analysis/
│
├── data/                # Raw and cleaned datasets  
├── notebooks/           # EDA and model-building notebooks  
├── visuals/             # Charts and plots  
├── report/              # Full PDF report  
└── README.md            # Project documentation  

👤 Author

Deepak Malviya
Data Analyst
