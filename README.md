# Airline Reviews Analysis

## Overview
This project explores which aspects of a flight experience influence a customer's likelihood to recommend an airline. Using over 23,000 verified flight reviews from Kaggle, we applied Decision Tree and Random Forest models to classify customer recommendations based on various service and experience ratings.

Prepared by: Vy Nguyen, Dennis Wu, Kenjee Koh, Hsiang-Han Huang, Becky Wang

Key results include:
- Random Forest achieved 95% accuracy with full preprocessing and tuning
- "Value for Money", "Ground Service", and "Cabin Staff Service" were the top 3 drivers of customer recommendation
- SMOTE helped resolve class imbalance and improve model performance for minority class (recommendation = yes)

## Dataset
- **Source:** Kaggle (originally scraped from airlinequality.com by Juhi Bhojani)  
- **Scope:** 23,171 verified airline reviews  
- **Size:** 23,171 records × 19 attributes  
- **Target Variable:** Whether a reviewer recommended the airline (Yes/No)  

### 📋 Data Dictionary

| Feature                 | Definition                                                             | Data Type     |
|-------------------------|------------------------------------------------------------------------|---------------|
| Value for Money         | Customer rating of price relative to experience                        | Numerical (1–5)|
| Ground Service          | Rating of service received at the airport                              | Numerical (1–5)|
| Cabin Staff Service     | Rating of crew friendliness and service quality                        | Numerical (1–5)|
| Seat Comfort            | Comfort level of the seating experience                                | Numerical (1–5)|
| Inflight Entertainment  | Availability and quality of onboard entertainment                      | Numerical (1–5)|
| Food & Beverages        | Quality of food and drinks served during the flight                    | Numerical (1–5)|
| Wifi & Connectivity     | Availability and reliability of onboard internet                       | Numerical (1–5)|
| Seat Type               | Type of seat class (e.g., Economy, Premium, Business, First)           | Categorical (encoded) |
| Type of Traveller       | Purpose of travel (e.g., Solo, Business, Family)                       | Categorical (encoded) |
| Recommended             | Whether the customer recommends the airline (target variable)          | Binary (0/1)   |

## Tools & Methodology Overview
**Languages and Libraries:** Python (pandas, numpy, matplotlib, seaborn, scikit-learn, imblearn)

### Data Preprocessing:
- Dropped irrelevant columns (e.g., Review Date, Text Review, Aircraft)
- Encoded categorical variables (`Seat Type`, `Type of Traveller`) using label encoding
- Filled missing rating values with neutral score (3.0)
- Dropped rows with unverified reviewers or missing non-rating data
- Balanced dataset using SMOTE to resolve target class imbalance
- Converted `Recommended` variable into binary format (Yes = 1, No = 0)

### Modeling Techniques:
- Trained Decision Tree and Random Forest classifiers
- Compared benchmark models (minimal preprocessing) and full models (enhanced cleaning + tuning)
- Applied hyperparameter tuning (GridSearchCV / RandomizedSearchCV)
- Evaluated feature importance to understand drivers of recommendation

### Evaluation Metrics:
- Accuracy, Precision, Recall, F1-score
- Confusion Matrix (class-specific performance)
- Feature Importance (model interpretation)

## Highlighted Visualizations

**Distribution of Value for Money:**
![Value for Money Distribution](Notebooks/value_for_money_distribution.png)

**Confusion Matrix (Random Forest):**
![Confusion Matrix](Notebooks/confusion_matrix_random_forest.png)

## Results & Key Insights
- **Random Forest** with full preprocessing achieved the highest accuracy: **95%**
- **Value for Money** is the strongest driver of customer recommendations across all models
- **Ground Service** and **Cabin Staff Service** consistently ranked in the top 3 features
- SMOTE improved performance on the minority class (recommend = Yes)
- **Decision Trees** provided strong interpretability with slightly lower accuracy

## Key Deliverables
- Jupyter Notebooks:
  - `Notebooks/Airline_Reviews_Preprocessing.ipynb`
  - `Notebooks/Airline_Reviews_Decision_Tree_Models.ipynb`
  - `Notebooks/Airline_Reviews_Random_Tree_Models.ipynb`
- Final Report PDF: `Reports/Airline_Reviews_Analysis_Project_Report.pdf`

## What I Learned
- Preprocessing has a significant impact on tree model performance, especially with class imbalance
- Label encoding is effective when there’s ordinal meaning in categorical variables
- SMOTE can boost minority class precision without harming overall accuracy
- Tree-based models are intuitive but benefit greatly from tuning and structured input

## What I Plan to Improve
- Apply other ensemble models like XGBoost or Gradient Boosting for comparison
- Explore sentiment or topic modeling with the textual review data using NLP
- Integrate time-based analysis by leveraging review dates (e.g., trends over time)

## About Me
Hi, I’m Vy Nguyen and I’m currently pursuing my MS in Business Analytics at UC Irvine. I’m passionate about data analytics in Finance and Investment. Connect with me on [LinkedIn](https://www.linkedin.com/in/vy-ngoc-lan-nguyen).
