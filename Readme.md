# 🛍️ Customer Segmentation & High-Value Customer Prediction

## 📌 Project Overview

This project analyses customer purchasing behaviour using Python and Machine Learning to identify valuable customer segments and predict high-value customers. The objective is to help businesses improve customer retention, optimize marketing campaigns, and maximize revenue through data-driven decision making.

The project combines:

- SQL-based Business Analysis (MYSQL Workbench)
- Exploratory Data Analysis (EDA)
- Customer Segmentation using Clustering
- Predictive Modelling
- Feature Importance Analysis
- Interactive Dashboard Development (Tableau)
- Business Recommendations

---
# 🛠️ Tools & Technologies

### IDE
- VS Code
- Jupyter Notebook

### Programming & Analysis
- Python
- Pandas
- NumPy

### Data Visualization
- Matplotlib
- Seaborn
- Tableau

### Database
- MySQL Workbench

### Machine Learning
- Scikit-Learn


### Version Control
- Git
- GitHub

# 🛠️ Tech Stack

| Category | Tools & Technologies |
|----------|----------------------|
| Programming | Python |
| Data Manipulation | Pandas, NumPy |
| Data Visualization | Matplotlib, Seaborn, Tableau |
| Database | MySQL Workbench |
| Machine Learning | Scikit-Learn |
| Development Environment | VS Code, Jupyter Notebook |
| Version Control | Git, GitHub |

# 🎯 Business Objective

The primary objective is to:

- Identify customer purchasing patterns.
- Segment customers based on behavioural characteristics.
- Predict whether a customer is likely to become a High-Value Customer.
- Understand the most influential factors driving customer value.
- Generate actionable business insights for marketing and customer retention.

---


## 🗄️ SQL Business Analysis

Using MySQL Workbench, I solved business-oriented SQL problems to extract actionable insights from customer transaction data.

## 🗄️ SQL Business Analysis

SQL queries are documented in `Business SQL_Queries.md` along with brief business objectives, SQL concepts, and key insights for selected analytical problems.

The Markdown format was used to improve readability and provide business context alongside the SQL solutions.



### Key SQL Concepts Applied

- SELECT
- WHERE
- GROUP BY
- ORDER BY
- HAVING
- Aggregate Functions
- CASE Statements
- Window Functions
- Common Table Expressions (CTEs)
- Subqueries
- Joins


### Business Questions Solved
|Business Analysis Areas|Examples|
|------------------|------------|
|Customer Segmentation| Personas,Age Bins,Membership|
|Revenue Analysis| Revenue by Membership.revenue per visit|
|Customer Behaviour|Spending Patterns,Purchase Frequency|
|Customer value| CLV, High-value Customer|
|Adavanced SQL Analytics|Windows Functions,Percentiles,Quartiles,Rankings|

📄 **Complete SQL solutions are available in the `sql` folder.**


# 📂 Dataset Information

The dataset contains customer demographic and purchasing information.


### Features

| Feature | Description |
|----------|-------------|
| customer_id | Unique Customer ID |
| age | Customer Age |
| gender | Gender |
| city_tier | Customer's City Tier |
| membership_type | Membership Category |
| total_spend | Total Amount Spent |
| num_transactions | Number of Transactions |
| avg_transaction_value | Average Transaction Value |
| days_since_last_purchase | Recency of Purchase |
| num_visits | Website/Store Visits |
| product_categories_purchased | Number of Categories Purchased |
| discount_used | Discount Availed |
| high_value_customer | Target Variable (0/1) |

---






# 📊 Exploratory Data Analysis

Performed detailed EDA including:

- Missing Value Analysis
- Duplicate Detection
- Descriptive Statistics
- Distribution Analysis
- Correlation Analysis
- Customer Spending Patterns
- Membership-wise Analysis
- City Tier Analysis
- Purchase Behaviour Analysis

---

# 📈 Customer Segmentation

Applied clustering techniques to discover hidden customer groups.

### Clustering Workflow

- Data Cleaning
- Feature Scaling
- Optimal Cluster Selection
- K-Means Clustering
- Cluster Interpretation

Example customer segments:

- High Spending Loyal Customers
- Frequent Moderate Buyers
- Discount Driven Customers
- Low Engagement Customers

---

# 🤖 Machine Learning Model

Built a classification model to predict High Value Customers.

### Workflow

- Data Preprocessing
- Feature Encoding
- Train-Test Split
- Model Training
- Prediction
- Performance Evaluation

Evaluation metrics include:

- Accuracy
- Precision
- Recall
- F1 Score
- Confusion Matrix

# 📌 Feature Importance

Feature importance analysis was performed to understand which variables contribute the most towards predicting customer value.

Important drivers include:

- Total Spend
- Average Transaction Value
- Number of Transactions
- Membership Type
- Product Categories Purchased
- Customer Visits
- Days Since Last Purchase

These insights help businesses prioritize customer engagement strategies.

---

# 📊 Business Insights

Some of the key business findings include:

- Gold membership customers contribute significantly higher revenue.
- Customers with higher average transaction values are more likely to become high-value customers.
- Frequent purchasing behaviour strongly correlates with customer value.
- Recency is an important indicator of customer retention.
- Customers purchasing across multiple categories exhibit greater lifetime value.
- Discount-sensitive customers require different promotional strategies.

---

# 💡 Business Recommendations

Based on the analysis:

- Design personalized campaigns for high-value customers.
- Reward loyal customers through exclusive membership benefits.
- Re-engage inactive customers using targeted offers.
- Promote cross-selling to increase product category purchases.
- Identify customers at churn risk using predictive scores.
- Optimize promotional budgets based on customer segments.

---
 

# 📁 Repository Structure

```
Customer-Analytics-Business-Analysis/
│
├── README.md
│
├── data
│   └── cleaned_data.csv
│
├── sql
│   └── Business-SQL Queries.sql
│
├── python
│   └── customer_analytics.py
│   
|
├── tableau
│   ├── Customer_analytics.twb
│   
│
├── outputs
│   ├── dashboards/
│   │   ├── Executive_Summary.png
│   │   ├── Customer_Segmentation.png
│   │   ├── Customer_Value_Analysis.png
│   │   ├── Revenue_Analysis.png
│   │   ├── Customer-Engagement_Retention.png
│   │   └── Customer-Purchase_Correlation.png
│   │
│   ├── Exploratory Data Analysis()
│   │   ├── Age_Distribution.png
│   │   ├── Spending_Distribution.png
│   │   ├── Categorical_Features_Distribution.png
│   │   └── Box plot.png
│   │
│   ├── customer_segmentation
│   │   ├── Clusters.png
│   │   ├── Customer_Segmentation_Report.pdf
│   │   └── Confusion_Matrix.png
│   │
│   └── feature importance
│       ├── Feature_Importance_Analysis.png
│       └──  Feature_Importance_Plot.png
│
└── requirements.txt      
       
```


## 📂 Dataset

The original customer dataset was cleaned and preprocessed before analysis.

Data cleaning included:
- Handling missing values 
- Removing duplicate records 
- Preparing the dataset for SQL, Python, and Tableau analysis

All analyses in this repository are based on the cleaned dataset (`cleaned_data.csv`) to ensure consistency and accuracy across the project.

## 🚀 Future Improvements

- Deploy the predictive model using Streamlit or Flask.
- Build an interactive web application for business users.
- Automate data refresh and dashboard updates.
- Experiment with advanced ensemble models (e.g., XGBoost, LightGBM).
- Incorporate time-series analysis to forecast customer spending trends.
- Connect the project to cloud-based databases or data warehouses.

---


# 🔄 Project Workflow

Raw Dataset

↓

Data Cleaning & Preprocessing

↓

Exploratory Data Analysis (Python)

↓

Business Analysis using SQL

↓

Customer Segmentation & Machine Learning

↓

Interactive Dashboard Development (Tableau)

↓

Business Insights & Recommendations


---


# 🎯 Project Outcome

This project demonstrates an end-to-end analytics solution by integrating:

- ✔ SQL (MySQL Workbench) for business query analysis
- ✔ Python for data preprocessing, exploratory analysis, clustering, predictive modeling, and feature importance
- ✔ Tableau for interactive business dashboards and KPI visualization

---
