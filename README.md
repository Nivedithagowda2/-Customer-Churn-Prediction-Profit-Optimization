📊 Customer Churn Prediction & Profit Optimization
Scalable Machine Learning on 1 Million Customers

🚀 Project Overview

This project builds an end-to-end machine learning pipeline to predict customer churn and optimize retention strategy using a cost-sensitive business approach.

The model was trained on 1,000,000 customer records merged from 5 raw CSV files, simulating real-world large-scale production data.

The objective is not only to predict churn accurately, but to translate predictions into measurable financial impact.

🎯 Business Objective

Customer churn directly reduces company revenue.

Instead of applying retention campaigns to all customers (high cost), this solution:

Predicts churn probability

Segments customers into risk categories

Targets only high-risk users

Maximizes return on marketing investment

This transforms predictive modeling into a profit-optimization strategy.

🏷️ Target Variable Construction (Churn Definition)

Overview

The original dataset did not contain a predefined Churn column.
Therefore, the churn label was engineered using business logic based on customer activity patterns.

Churn prediction is framed as a binary classification problem, where:

1 → Customer churned (customer likely to leave)

0 → Customer retained (customer active)

Business Logic Used to Create Churn

A customer was marked as Churn = 1 if:

The customer had no transactions in the last 90 days

OR account status was inactive/closed

OR subscription was not renewed

Otherwise:

Customer was marked as Churn = 0

Example Logic (Code Implementation)
import pandas as pd
from datetime import datetime

# Load dataset
df = pd.read_csv("data.csv")

# Convert last transaction date to datetime
df["last_transaction_date"] = pd.to_datetime(df["last_transaction_date"])

# Define reference date (latest date in dataset)
reference_date = df["last_transaction_date"].max()

# Create churn column
df["Churn"] = (
    (reference_date - df["last_transaction_date"]).dt.days > 90
).astype(int)

Why 90 Days?

90 days is an industry-standard inactivity threshold

Helps balance false positives and false negatives

Suitable for subscription/transaction-based businesses

This threshold can be adjusted based on business requirements.

Class Distribution

After creating the churn column:

Total records: 1,000,000+ rows

Class imbalance handled using:

Class weights

SMOTE (if applied)

Cost-sensitive evaluation

Business Impact

Cost assumptions:

Cost of losing customer: $500

Cost of retention campaign: $20

Using churn prediction enables:

Targeted retention campaigns

Reduced revenue loss

Increased customer lifetime value

Profit-based model evaluation

📁 Dataset

Total records used for training: 1,000,000

Data source: 5 merged CSV files

Target variable: churn

Extensive feature engineering performed

Due to GitHub file size limitations, only a sample dataset (10,000 rows) is included in this repository (sample_data.csv) for demonstration purposes.

The full dataset was used during training and evaluation but is not uploaded.

⚙️ Technical Implementation

Data cleaning & preprocessing

Feature engineering (behavioral metrics, ratios, log features)

Classification model for churn prediction

Risk segmentation (Low / Medium / High)

Lift analysis

Top 20% churn capture strategy

SHAP-based model interpretability

Cost-sensitive profit simulation

📈 Model Insights

Overall churn rate: 61.8%

High-risk churn rate: 87.4%

Lift (High Risk vs Overall): 1.41x

Top 20% high-risk customers capture: 30.5% of total churners

The model demonstrates strong ranking power for identifying high-risk customers.

💰 Business Impact Simulation

To evaluate real-world value, a cost-sensitive retention strategy was simulated.

Assumptions

Total customers: 100,000

Overall churn rate: 61.8% → 61,800 churners

Top 20% captures 30.5% churners → 18,849 churners

Campaign cost per targeted customer: $20

Targeted customers: 20,000

Total campaign cost: $400,000

If the campaign successfully retains just 15% of targeted churners:

Saved customers: 2,827

Revenue saved per customer: $500

Total revenue saved: $1,413,500

📊 Net Profit

Net Profit = Revenue Saved − Campaign Cost

= $1,413,500 − $400,000
= $1,013,500 profit per 100,000 customers

This demonstrates how predictive modeling directly supports revenue optimization.

🧠 Key Business Insights

Inactivity and engagement patterns strongly influence churn.

Risk-based targeting significantly reduces marketing waste.

Data-driven retention campaigns can generate measurable ROI.

Predictive analytics improves strategic decision-making.

📦 Repository Structure
│   └── sample_data.csv
│   └── churn_model.ipynb
├── README.md
└── .gitignore

❌ Why No Frontend?

This project is designed for a Data Scientist role, focusing on:

Scalable model development

Performance evaluation

Model interpretability

Business impact analysis

Frontend deployment is not required to demonstrate core data science competency.

🏆 Skills Demonstrated

Large-scale data handling (1M+ records)

Feature engineering

Classification modeling

Risk segmentation

Lift & targeting analysis

SHAP interpretability

Cost-sensitive decision modeling

Business ROI estimation

✅ Conclusion

This project showcases a production-style, business-oriented Data Science workflow that bridges machine learning with financial impact.

The focus is not just model accuracy, but strategic decision-making and profit optimization.

👤 Author
Name: Niveditha
Niveditha GitHub: https://github.com/Nivedithagowda2
Linkedin: https://www.linkedin.com/in/niveditha-89ba04356/
