# Comparison of Model 1 and Model 2

## 1. Overview

This document compares the performance of the two classification models developed for the Bank Customer Churn Dataset:
Model 1: Logistic Regression
Model 2: Random Forest

Both models were evaluated using the same 2,000-observation test set. The comparison considers classification metrics, confusion matrices and probability-based performance through ROC-AUC.

## 2. Related Notebook

The performance comparison is contained in:
statistical_helpers/Comparison.ipynb

How to use the notebook:
- Ensure that the preprocessing and model notebooks have been executed.
- Ensure that both trained models and their test-set predictions are available.
- Open Comparison.ipynb in Jupyter Notebook or JupyterLab.
- Run the cells sequentially.
- The notebook calculates and displays the comparative performance metrics and probability-based measures.

## 3. Classification Performance

The two models produced exactly the same confusion matrix:

[[1591    1]

 [   2  406]]

The results are summarised below.

|Metric	| Model 1: Logistic Regression |	Model 2: Random Forest |
|-------|------------------------------|------------------------|
True Negatives |	1,591	               |  1,591 |
False Positives	|1	                   | 1 |
False Negatives	|2	                   | 2 |
True Positives	|406	                 | 406 |
Correct Predictions	|1,997.     	     | 1,997 |
Incorrect Predictions	|3	             | 3 |
Accuracy	|**99.85%**.     	           | **99.85%** |
Precision – Class 0 |	1.00	           | 1.00 |
Recall – Class 0	| 1.00	             | 1.00 |
F1-score – Class 0	| 1.00	           | 1.00 |
Precision – Class 1 |	1.00	           | 1.00 |
Recall – Class 1 |	1.00	             | 1.00 |
F1-score – Class 1 |	1.00	           | 1.00 |
