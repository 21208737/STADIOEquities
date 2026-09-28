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

## 4. Confusion Matrix Comparison

The confusion matrices are identical:

Model 1 – Logistic Regression
[[1591    1]
 [   2  406]]

Model 2 – Random Forest
[[1591    1]
 [   2  406]]

Both models therefore produced:
1,591 true negatives
1 false positive
2 false negatives
406 true positives

Both models correctly classified 1,997 out of 2,000 observations.This results in an accuracy of: 99.85%

## 5. Interpretation of the Identical Predictions

It is not always the case that the models' underlying probability estimates are the same only because they produced the same class predictions at the chosen threshold.
A threshold is used to transform anticipated probabilities into class predictions for binary classification. The normal threshold of 0.5 was applied in this analysis.

Probability < 0.5 → Predicted class 0 
Probability ≥ 0.5 → Predicted class 1

As a result, two models can assign each observation to the same final class yet yield different probability estimates.
For instance, a chance of 0.95 from one model and 0.55 from another would both lead to: Class prediction = 1
As a result, the identical confusion matrices do not prove that the probability-based performance of the two models is the same.

## 6. ROC-AUC Comparison

ROC-AUC should therefore be used to examine the probability outputs from the two models.

The Model 1 ROC-AUC is calculated using:

y_prob_logistic1 = model1.predict_proba(X_test_scaled)[:, 1]

auc_model1 = roc_auc_score(
    y_test,
    y_prob_logistic1
)

The Model 2 ROC-AUC is calculated using:

y_prob_rf2 = model2.predict_proba(X_test)[:, 1]

auc_model2 = roc_auc_score(
    y_test,
    y_prob_rf2
)

| Metric |	Logistic Regression |	Random Forest |
| -------| --------------------| --------------|
| Accuracy |	99.85%            |	99.85% |
| Precision |	1.00 |	1.00 |
| Recall	| 1.00 |	1.00 |
| F1-score	| 1.00 |	1.00 |
| ROC-AUC	 | 0.9992 |	0.5067 |
