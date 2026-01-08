# Exploratory Data Analysis (EDA) – Fraud Detection Capstone

## Purpose of This Document

This README summarizes the **Exploratory Data Analysis (EDA)** conducted as part of the Fraud Detection Capstone Project. The objective of the EDA was to understand the structure, quality, and measurable behavioral patterns present in the transaction data prior to applying machine learning models.

All conclusions presented in this document are grounded in **observed distributions, proportions, and patterns** derived directly from the dataset and validated through the accompanying Jupyter notebooks.

---

## Dataset Overview

The dataset consists of **50,000 transaction records** with **21 total features**, representing transaction-level financial activity with a binary fraud indicator. Each row corresponds to a single transaction, and features capture monetary value, temporal context, device and location information, merchant attributes, and user behavior.

### Quantitative Summary

- **Total transactions:** 50,000
- **Fraudulent transactions:** \~16,067 (**32.13%**)
- **Non-fraudulent transactions:** \~33,933 (**67.87%**)
- **Target variable:** `Fraud_Label` (0 = non-fraud, 1 = fraud)
- **Feature types:**
  - Numerical (e.g., Transaction Amount, Account Balance, Risk Score)
  - Categorical (e.g., Transaction Type, Merchant Category, Device Type)
  - Temporal (e.g., Timestamp, Is\_Weekend)

This distribution reflects a **moderately imbalanced fraud dataset**.

---

## 1. Target Variable Analysis (Fraud vs Non-Fraud)

### What Was Analyzed

- Absolute and relative distribution of fraudulent vs non-fraudulent transactions
- Degree of class imbalance

### Key Findings

- Fraud represents **32.13%** of all transactions
- Non-fraudulent transactions remain the majority class

### Conclusion

- The observed imbalance justified:
  - **Recall** to measure missed fraud
  - **Precision** to control false alerts
  - **F1-Score and ROC AUC** as balanced performance metrics
  - **SMOTE and stratified sampling** to prevent model bias toward the majority class

---

## 2. Transaction Amount Analysis

### What Was Analyzed

- Distribution of `Transaction_Amount`
- Comparison of transaction amounts between fraudulent and non-fraudulent cases

### Key Findings

- Transaction amounts span a **wide numeric range**, reflecting heterogeneous spending behavior
- Fraudulent transactions exhibit **higher variance and more extreme values**
- Legitimate transactions cluster more tightly around lower-to-moderate amounts

### Conclusion

- Absolute transaction amount alone does not reliably separate fraud from non-fraud

---

## 3. Transaction Amount-to-Balance Ratio

### What Was Analyzed

- Ratio of `Transaction_Amount` to `Account_Balance`
- Differences in ratio behavior between fraud and non-fraud transactions

### Key Findings

- Fraudulent transactions consistently show **higher and more volatile ratios**
- Non-fraud transactions remain concentrated within **narrower ratio ranges**

### Conclusion

- Relative spending behavior provides stronger signal than absolute amounts

---

## 4. Temporal Analysis (Time-Based Patterns)

### What Was Analyzed

- Transaction volume by hour of day
- Fraud frequency across time
- Weekend vs weekday behavior (`Is_Weekend`)

### Key Findings

- Fraud is **unevenly distributed across hours of the day**
- Certain low-activity periods show a **higher proportion of fraudulent transactions**
- Weekend transactions exhibit **different fraud dynamics** compared to weekdays

### Conclusion

- Fraud risk is influenced by temporal context rather than occurring uniformly
- Time-based features may add incremental predictive power when combined with behavioral signals

---

## 5. Merchant Category Analysis

### What Was Analyzed

- Transaction volume by merchant category
- Fraud rates within each category

### Key Findings

- Certain merchant categories exhibit **disproportionately higher fraud rates**
- Other categories demonstrate consistently low fraud prevalence

### Conclusion

- Merchant category acts as a meaningful contextual risk indicator
- These patterns support risk segmentation and category-specific fraud controls

---

## 6. Feature Distribution and Outlier Behavior

### What Was Analyzed

- Distribution shapes of numerical features
- Presence of skewness and extreme values

### Key Findings

- Many numerical features are **right-skewed**
- Outliers are more prevalent among fraudulent transactions

### &#x20;Conclusion

- &#x20;Scaling and normalization would be required for addressing Skewed distributions
- This observation supports the effectiveness of tree-based and ensemble methods over linear models

---

## 7. Correlation and Feature Interaction Insights

### What Was Analyzed

- Pairwise correlations among numerical features
- Relationships between individual features and fraud outcome

### Key Findings

- No single feature shows a dominant linear relationship with fraud
- Fraud emerges from **interactions among multiple features**

### Why This Matters (Data-Driven Conclusion)

- Linear decision boundaries are insufficient for this problem
- Capturing feature interactions is essential for strong performance

---

## Overall EDA Conclusions

The EDA confirms that fraud in this dataset is a **multi-dimensional behavioral phenomenon** driven by relative spending behavior, temporal context, merchant characteristics, and complex feature interactions. No single variable sufficiently explains fraud risk.

Observed data patterns directly informed the modeling approach:

- Application of **SMOTE** to counter class imbalance
- Selection of **Recall, Precision, F1-Score, and ROC AUC** as primary metrics
- Emphasis on **ensemble learning methods** capable of capturing non-linear interactions
- Inclusion of **ratio-based and temporal features**

---

##
