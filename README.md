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
- Identified **high-propensity** individuals (top 20%) within this group.
- Analyzed their characteristics to derive **actionable marketing insights**.

---

## Key Results and Insights

### Model Performance (Tuned Model on Unseen Test Set)

| Metric                      | Value   |
|----------------------------|---------|
| ROC AUC Score              | 0.6242  |
| Accuracy                   | 0.7636  |
| Precision (for members)    | 0.5909  |
| Recall (for members)       | 0.0027  |
| F1-Score (for members)     | 0.0055  |

**Note on Performance**:  
The low **Recall** and **F1-Score** for the `1.0` class (members) indicate that while the model has decent **overall accuracy and precision**, it struggles to identify a large proportion of actual members.  
This is **common in highly imbalanced datasets** where the member class is the minority. The default classification threshold (0.5) may not be optimal — further tuning or the use of **imbalanced learning techniques** (e.g., SMOTE, class weighting, threshold adjustment) could improve performance.

---

### Targeting 18–30 Year Olds (Tuned Model)

- **Total 18–30 year olds in test set**: 4,864
- **Propensity threshold for 'high-propensity' (top 20%)**: 0.3735
- **Number of 'high-propensity' 18–30 year olds**: 973

#### Characteristics of High-Propensity 18–30 Year Olds:
- **Online Channels**:
  - Social: 28.37%
  - Organic Search: 22.20%
  - Paid Search: 17.88%
- **Favorite Product Categories**:
  - Fresh Produce: 27.75%
  - Ready Meals: 23.02%
- **Average Behavior**:
  - Online: ~15.77 page views, ~302.75 seconds session duration  
  - In-store: ~£24.87 weekly spend, ~1.79 weekly visits

---

## Actionable Marketing Insights

Based on the simulation, the supermarket could consider the following:

- **Target**:  
  Focus acquisition efforts on **18–30 year olds** with a predicted propensity score **≥ 0.37**.

- **Messaging**:  
  Personalize messaging by highlighting:
  - Discounts on **Ready Meals**
  - **Sustainability initiatives**, if indicated as a driver by important features

- **Channels**:  
  Prioritise digital channels — especially **Social Media** — to reach this segment effectively.

---
