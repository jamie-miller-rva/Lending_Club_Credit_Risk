# Lending Club Credit Risk Analysis

## Background:
Credit risk is an inherently unbalanced classification problem, as good loans easily outnumber risky loans.

## Overview of the analysis:
The goal of this supervised machine learning problem is to classifiy future (unseen) loans as either "low_risk" or "high_risk." A dataset consistsing of ~69k applications is used to train and evaluate several machine learning models. The dataset was almost entirely composed of "low_risk" loans while only 347 were categorized as "high_risk" loans. The feature matrix was composed over 85 variables consisting of numeric and categorical values (that required preprocessing using the get_dummies method prior to modeling).

The analysis was composed of two parts: Resampling Models to Predict Credit Risk and Ensemble Classifiers to Predict Credit Risk (each contained in its own Juypter Notebook).

## Deliverable 1: Use Resampling Models to Predict Credit Risk
This analysis used multiple techniques (from the imbalanced-learn library) to address the unbalanced nature of the target variable to included Oversampling, Undersampling and a Combination to the two.

* The RandomOverSampler module was used to to oversample the minority class to generate new "high_risk" loan cases by randomly sampling with replacement the current available samples.
* The Synthetic Minority Oversampling Technique (SMOTE) moduel was used to oversample the minority class to generate new samples by interpolation.
* The ClusterCentroids module was used to undersample the majority class making use of K-means to reduce the number of samples.

Each resampled dataset was then modeled using Logistic Regression and predictions from the model were assessed using a balanced accuracy score, a confusion matrix and an imbalanced classification report.

Results for Resampling Models to Predict Credit Risk:

* The Logistic Regression Classifier using Random Oversampling had a balanced_accuracy_score of 0.647; however, it is not suitable for high_risk loans as indicated by the low precision score (0.01) and low f1 score (0.02)
* The Logistic Regression Classifier using Synthetic Minority Oversampling Technique (SMOTE) had a balanced_accuracy_score of 0.662; however, it was not suitable for high_risk loans as indicated by the low percision score(0.01) and low f1 score (0.02)
* The  Logistic Regression Classifier using ClusterCentroids to undersample had a balanced_accuracy_score of 0.545; however it is not suitable for high_risk loans as indicated by the low percision score (0.01) and low f1 score (0.01)

Summary for Resampling Models to Predict Credit Risk: No technique of oversampling, undersampling or a combination was found to addequaltely addressed this unbalanced classification problem using a Logistic Regression Model therefore there is no model recommendation.

## Deliverable 2: Use the SMOTEENN algorithm to Predict Credit Risk 

This analysis used the SMOTEENN technique (from the imbalanced-learn library) to address the unbalanced nature of the target variable. The SMOTE technique used in part one is known to generate noisy samples by interpolating new points between marginal outliers and inliers. This issue can be solved using the SMOTEENN technique which cleans the space resulting from over-sampling.

The resampled dataset was modeled using Logistic Regression and predictions from the model were assessed using a balanced accuracy score, a confusion matrix and an imbalanced classification report.

Results for Resampling Models to Predict Credit Risk:

* The Logistic Regression Classifier using the SMOTEENN algorithm combining over- and undersampling methods had a balanced_accuracy_score of  0.630; however, it is not suitable for high_risk loans as indicated by the low percision score (0.01) and low f1 score (0.02)
  

## Deliverable 3: Use Ensemble Classifiers to Predict Credit Risk
This part of the analysis used the BalancedRandomForestClassifier and EasyEnsembleClassifier modules(from the imbalanced-learn library) to avoid the pitfalls of favoring the majority classes by allowing for the balancing of each subset of data.

Results for Ensemble Classifiers to Predict Credit Risk: 

* BalancedRandomForestClassifier is an ensemble method in which each tree of the forest will be provided a balanced bootstrap sample. The balanced_accuracy_score was 0.789; however, it is not suitable for high_risk loans as indicated by the low precision score (0.03) and low f1 score (0.06)
* EasyEnsembleClassifier uses AdaBoostClassifier as learners which are trained on balanced bootstrap samples. The balanced_accuracy_score was 0.932; however, it is not suitable for high_risk loans as indicated by the low precision score (0.09) and low f1 score (0.16)

Summary for Ensemble Classifiers to Predict Credit Risk: No technique of bagging or boosting was found to addequaltely addressed this unbalanced classification problem therefore there is no model recommendation.






