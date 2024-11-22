# Time Series Classification and Feature Extraction

This repository contains a detailed analysis and implementation of feature extraction and classification for time series data. The project focuses on human activity classification based on time series data obtained from a Wireless Sensor Network, as provided in the **AReM dataset**.

---

## Table of Contents

- [Introduction](#introduction)
- [Data](#data)
- [Project Tasks](#project-tasks)
  - [Feature Creation/Extraction](#feature-creationextraction)
  - [Binary Classification Using Logistic Regression](#binary-classification-using-logistic-regression)
  - [L1-Penalized Logistic Regression](#l1-penalized-logistic-regression)
  - [Multi-class Classification](#multi-class-classification)
- [Results](#results)

---

## Introduction

This project explores **time series classification**, a common machine learning task. The goal is to classify human activities based on time-domain features extracted from multivariate time series data. The project includes binary classification, feature engineering, and multiclass classification using logistic regression, penalized regression, and Naïve Bayes classifiers.

---

## Data

The **Activity Recognition System based on Multisensor Data Fusion (AReM)** dataset is publicly available at the UCI Machine Learning Repository:

[AReM Dataset](https://archive.ics.uci.edu/ml/datasets/Activity+Recognition+system+based+on+Multisensor+data+fusion+%28AReM%29)

### Dataset Structure:
- **Folders**: 7 folders represent seven activities:
  - Bending1, Bending2, Cycling, Lying, Sitting, Standing, Walking.
- **Files**: Each file represents a single instance of an activity and contains six time series:
  - avg rss12, var rss12, avg rss13, var rss13, avg rss23, var rss23.
- **Statistics**:
  - Total instances: 88
  - Length of each time series: 480 values.

---

## Project Tasks

### Feature Creation/Extraction
1. **Data Splitting**:
   - Use datasets 1 and 2 from *Bending1* and *Bending2*, and datasets 1, 2, and 3 from other folders for testing.
   - Use the remaining datasets for training.

2. **Time-Domain Features**:
   - Research common time-domain features for time series classification, including:
     - Minimum, Maximum, Mean, Median, Standard Deviation, Quartiles, etc.
   - Extract the following features for all six time series:
     - Minimum, Maximum, Mean, Median, Standard Deviation, First Quartile, Third Quartile.
   - Resulting Dataset:
     | Instance | min1 | max1 | mean1 | median1 | ... | 1st_quart6 | 3rd_quart6 |
     |----------|------|------|-------|---------|-----|------------|------------|

3. **Bootstrap Confidence Intervals**:
   - Compute the standard deviation of each feature.
   - Use bootstrapping to create 90% confidence intervals for the standard deviation.

4. **Feature Selection**:
   - Select three most important time-domain features for further analysis.

---

### Binary Classification Using Logistic Regression
1. **Visual Exploration**:
   - Scatterplots of the selected features from time series 1, 2, and 6, distinguishing between bending and other activities.

2. **Feature Expansion**:
   - Break each time series into two halves, creating 12 time series per instance. Repeat scatterplots for the expanded features.

3. **Optimal Time-Series Segmentation**:
   - Experiment with segmenting each time series into \( l \in \{1, 2, ..., 20\} \) equal-length series.
   - Use logistic regression to solve the binary classification problem for each segmentation.
   - Perform feature selection based on p-values or recursive feature elimination.

4. **Performance Metrics**:
   - Confusion Matrix, ROC Curve, AUC, Logistic Regression Coefficients, and p-values.

5. **Class Imbalance**:
   - Address class imbalance using case-control sampling.
   - Adjust parameters and report performance metrics.

---

### L1-Penalized Logistic Regression
1. **Feature Selection with Regularization**:
   - Repeat the binary classification task using L1-penalized logistic regression.
   - Perform cross-validation to optimize \( l \) (number of segments) and \( \lambda \) (penalty weight).

2. **Comparison**:
   - Compare L1-penalized logistic regression with feature selection based on p-values.
   - Assess ease of implementation and model performance.

---

### Multi-class Classification
1. **L1-Penalized Multinomial Regression**:
   - Use the optimal \( l \) from previous tasks.
   - Train a multinomial regression model for all activities and evaluate performance.

2. **Naïve Bayes Classification**:
   - Use both Gaussian and Multinomial priors to classify activities.
   - Compare performance with multinomial regression.

3. **Performance Metrics**:
   - Report confusion matrix, ROC curves, and test errors for multi-class classification.

---

## Results

- **Feature Engineering**:
  - Extracted time-domain features and selected the most significant ones.
- **Binary Classification**:
  - Identified optimal segmentation (\( l \)) and feature selection methods.
- **Multi-class Classification**:
  - Compared logistic regression and Naïve Bayes models.

---
