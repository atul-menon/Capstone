# Capstone Project: Fraud Detection Model Evaluation

## Project Overview

Fraud detection is a critical challenge in financial systems, where the objective is to accurately identify fraudulent transactions while minimizing false alarms that negatively impact legitimate customers. This project evaluates and compares multiple machine learning classification models to determine which approaches are most effective for detecting fraud in an imbalanced dataset.

The analysis contrasts **linear models**, **instance-based learning**, and **ensemble-based methods** to understand trade-offs between accuracy, recall, precision, stability, and real-world applicability. The ultimate goal is to recommend models best suited for deployment in production-grade fraud detection systems.

---

## Problem Statement

Fraud datasets are inherently **highly imbalanced**, with fraudulent transactions representing only a small percentage of total activity. This imbalance introduces two key challenges:

- **False negatives (missed fraud)** can result in direct financial loss.
- **False positives (incorrect fraud flags)** can degrade customer trust and experience.

This project aims to answer the following questions:

- Which machine learning models most effectively detect fraudulent activity?
- How do models balance recall and precision in an imbalanced setting?
- Which approaches generalize well to unseen data?

---

## Technical Deliverables

The technical component of this capstone is delivered as a **collection of Jupyter Notebook, readme.md file and sample dataset ** that document the full analytical workflow, including:

- Data loading and validation
- Exploratory data analysis (EDA)
- Feature engineering and preprocessing
- Class imbalance handling
- Feature selection
- Model training, cross-validation, and evaluation

The notebook includes **clear section headers, inline comments, and structured code** to ensure transparency and reproducibility of the analysis.

---

## Models Evaluated

The following classification models were trained and evaluated:

- Logistic Regression
- SGD Classifier
- K-Nearest Neighbors (KNN)
- Random Forest
- AdaBoost
- Gradient Boosting
- XGBoost

---

## Results Summary

The table below summarizes the updated performance metrics for each model.

### Model Performance Summary

| Metric | Logistic Regression | SGD Classifier | KNN | Random Forest | AdaBoost | Gradient Boosting | XGBoost |
|------|---------------------|---------------|-----|---------------|----------|------------------|---------|
| **Accuracy** | 0.7184 | 0.7931 | 0.5849 | **1.0000** | 0.9990 | **1.0000** | 0.9988 |
| **Precision** | 0.5478 | 0.6574 | 0.4022 | **1.0000** | 0.9969 | **1.0000** | 0.9988 |
| **Recall** | 0.7678 | 0.7598 | 0.5683 | **1.0000** | **1.0000** | **1.0000** | 0.9975 |
| **F1-Score** | 0.6394 | 0.7049 | 0.4710 | **1.0000** | 0.9985 | **1.0000** | 0.9982 |
| **ROC AUC** | 0.8189 | 0.8908 | 0.6056 | **1.0000** | **1.0000** | **1.0000** | 0.999995 |
| **False Positives** | 2,061 | 1,288 | 2,747 | **0** | 10 | **0** | 4 |
| **False Negatives** | 755 | 781 | 1,404 | **0** | **0** | **0** | 8 |
| **Avg Training CV Score** | 0.8108 | 0.8844 | 0.6757 | 0.9952 | 0.9932 | **0.9996** | **0.9996** |
| **Training CV Std Dev** | 0.0095 | 0.0020 | 0.0070 | 0.0010 | 0.0008 | **0.0002** | **0.0001** |

---

## Key Findings (Non-Technical Summary)

### Ensemble Models Deliver Superior Performance

**Random Forest and Gradient Boosting** achieved perfect classification results, with zero false positives and zero false negatives. Their performance across all metrics—including ROC AUC and cross-validation stability—indicates exceptional reliability and strong generalization.

**XGBoost** closely matched this performance, producing near-perfect results with only a minimal number of misclassifications while maintaining excellent stability across validation folds.

**AdaBoost** also performed exceptionally well, achieving near-perfect accuracy and recall with only a small number of false positives, making it a strong candidate when balancing performance and computational efficiency.

---

### Linear Models Provide Stability but Limited Accuracy

**Logistic Regression** and **SGDClassifier** showed moderate performance. While recall remained reasonable, both models suffered from lower precision and a higher number of false positives, limiting their suitability for production fraud detection systems where customer experience is critical. These models remain valuable primarily for baseline comparisons and interpretability-focused use cases.

---

### KNN Underperformed in High-Stakes Fraud Detection

**K-Nearest Neighbors (KNN)** delivered the weakest results across nearly all metrics, with lower accuracy, ROC AUC, and a high number of both false positives and false negatives. This indicates limited effectiveness for complex, high-dimensional fraud detection tasks without significant tuning or feature refinement.

---

## Recommendations

Based on the updated results:

- **Primary Recommendation:** Deploy **ensemble-based models** such as Random Forest, Gradient Boosting, or XGBoost for fraud detection systems requiring high accuracy and reliability.
- **Production-Ready Choice:** XGBoost offers an excellent balance of near-perfect performance, robustness, and scalability.

---

## Conclusion

This updated analysis reinforces that **ensemble learning methods** are the most effective approach for fraud detection in imbalanced datasets. Their ability to capture complex patterns, minimize costly errors, and generalize consistently makes them the preferred choice for real-world financial risk mitigation systems.

