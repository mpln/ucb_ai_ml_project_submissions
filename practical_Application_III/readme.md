# Bank Marketing Campaign Analysis: Comparing Classification Models

## Summary

This analysis evaluates four machine learning classifiers (Logistic Regression, K-Nearest Neighbors, Decision Trees, and Support Vector Machines) to predict customer subscription to term deposits.

## Business Problem Statement

**Objective**: The task is to develop a predictive model that can effectively identify which bank clients are more likely to subscribe to a term deposit.

**Business Impact**: Improved targeting can reduce campaign costs and increase conversion rates.

## Data Understanding & Descriptive Statistics

### Dataset Overview

- Dataset represents 17 marketing campaigns (May 2008 - November 2010)
- **Size**: 41,188 records with 21 features
- **Target Variable**: `y` (Binary)
- **Class Distribution**: Imbalanced
  - No subscription: 89%
  - Subscription: 11%

### Feature Engineering Applied

1. **Removed duration feature**
2. **Binary encoding**: pdays (999 → 0, others → 1) for "previously contacted"
3. **One-hot encoding**: 10 categorical features → 43 binary features
4. **Feature scaling**: StandardScaler applied to 9 numerical features

## Model Performance Analysis

### Baseline Performance

- **Dummy Classifier (Most Frequent)**: 88.74% accuracy
- **Interpretation**: Simply predicting "no subscription" for all customers achieves high accuracy due to class imbalance

### Model Comparison Results (without hyperparameter tuned)


| Model                      | Train Time (sec) | Train Accuracy | Test Accuracy |
| ---------------------------- | ------------------ | ---------------- | --------------- |
| **Baseline**               | -                | 88.74%         | 88.74%        |
| **Logistic Regression**    | 0.09             | 90.0%          | 90.0%         |
| **K-Nearest Neighbors**    | 0.00             | 91.0%          | 89.0%         |
| **Decision Tree**          | 0.74             | 100.0%         | 84.0%         |
| **Support Vector Machine** | 59.78            | 90.0%          | 90.0%         |

### Model Comparison Results (with hyperparameter tuned)


| Model                      | Train Time (sec) | Train Accuracy | Test Accuracy | CV Score | Best Parameters                                       |
| ---------------------------- | ------------------ | ---------------- | --------------- | ---------- | ------------------------------------------------------- |
| **Baseline**               | -                | 88.74%         | 88.74%        | -        | Most frequent prediction                              |
| **Logistic Regression**    | 30.71            | 83.0%          | 83.0%         | 0.63     | C=0.1, class_weight='balanced', solver='liblinear'    |
| **K-Nearest Neighbors**    | 212.54           | 100.0%         | 88.0%         | 0.30     | n_neighbors=3, weights='distance', metric='euclidean' |
| **Decision Tree**          | 7.56             | 85.0%          | 85.0%         | 0.61     | max_depth=5, class_weight='balanced'                  |
| **Support Vector Machine** | 5495.20          | 93.0%          | 90.0%         | 0.25     | C=10, kernel='rbf', gamma='scale'                     |

### Performance Insights

**Best Accuracy**: SVM achieves 90% test accuracy in both scenarios but with drastically different training times.

**Efficiency Leader**: Decision Tree provides the best speed-accuracy balance (7.56 sec, 85% accuracy) after tuning.

**Hyperparameter Impact**:

- **Decision Tree**: Improved from 84% to 85%, and eliminated overfitting
- **SVM**: Same accuracy (90%) but training time increased 92x (60 sec → 5495 sec)
- **Logistic Regression**: Accuracy dropped from 90% to 83% due to class balancing
- **KNN**: Persistent overfitting issues despite tuning

**Cross-Validation Reliability**: Logistic Regression (0.63) > Decision Tree (0.61) > KNN (0.30) > SVM (0.25)

**Production Recommendation**: Decision Tree for optimal balance of speed, accuracy, and interpretability.
