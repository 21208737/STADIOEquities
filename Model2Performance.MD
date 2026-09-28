# Overview

## 1. Summary

In order to forecast if a bank customer will leave the bank, Model 2 was constructed using a Random Forest classifier.
Exited was the target variable, where:
0 = retained customer
1 = customer churned or left

A test set with 2,000 observations was used to assess the model.

A confusion matrix and classification metrics were employed in the performance assessment. Because the model generates probability estimates that may be assessed independently of the chosen 0.5 classification threshold, ROC-AUC was also taken into consideration.

## 2. Related Notebook

The Model 2 implementation and performance calculations are contained in:
statistical_helpers/Model2Performance.ipynb

How to use the notebook:
- Ensure that the required Python packages listed in requirements.txt are installed.
- Ensure that the Bank Customer Churn Dataset is available in the specified dataset directory.
- Open Model2Performance.ipynb in Jupyter Notebook or JupyterLab.
- Run the notebook cells sequentially.
- The notebook performs the Model 2 prediction and calculates the relevant performance metrics.

## 3. Evaluation Metrics

The following measures were used:
Accuracy
Precision
Recall
F1-score
Confusion Matrix
ROC-AUC

These metrics offer supplementary data regarding the classification performance of the model. Because it is not dependent on a single classification threshold, the ROC-AUC measure is very useful when comparing probability outputs.

## 4. Confusion Matrix

The Random Forest model produced the following confusion matrix:
[[1591    1]
 [   2  406]]

