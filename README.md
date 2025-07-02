# LightGBM Model for Predicting Customer Membership Propensity (*Supermarket Membership Case Study*)

This Jupyter script demonstrates the process of building and tuning a LightGBM Gradient Boosting model to predict customer membership propensity for a supermarket, specifically focusing on targeting **18–30 year old** demographic

---

## Script Overview

The script covers the following steps:

### 1. Synthetic Data Generation
A dataset was created simulating:
- Customer demographics
- Online shopping behavior (GA4-like data)
- In-store transaction data  
This dataset includes a **binary target variable** indicating whether a customer is a member.

### 2. Data Preprocessing
- Categorical features were **one-hot encoded**.
- The dataset was **split into training and testing sets**.

### 3. Hyperparameter Tuning with GridSearchCV
A `GridSearchCV` was employed to systematically search for the optimal combination of **LightGBM hyperparameters**, including:
- `n_estimators`
- `learning_rate`
- `num_leaves`
- `max_depth`
- Regularization parameters  

The search used **5-fold cross-validation**, optimizing for **ROC AUC score**.

### 4. Model Training and Evaluation
- The LightGBM model was trained on the synthetic data using the **best hyperparameters**.
- Performance was evaluated on an **unseen test set** using the following metrics:
  - **ROC AUC**
  - **Accuracy**
  - **Precision**
  - **Recall**
  - **F1-Score**

### 5. Feature Importance Analysis
The script extracted and visualized **feature importances** to understand which features were most influential in predicting membership propensity.

### 6. Targeting Simulation for 18–30 Year Olds
- The model predicted **membership propensity** for 18–30 year olds in the test set.
- Identified **high-propensity** indiv
