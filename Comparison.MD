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

ROC-AUC values should not be inferred from the classification report because the classification report is based on the final class predictions, whereas ROC-AUC uses the probability scores.

## 7. Probability-Based Comparison

The two models were also compared using their predicted probabilities.
A non-zero probability difference would demonstrate that the models assign different probability values even though the 0.5 threshold produces the same class predictions.

However, this were the results of the Probability-Based Comparison: 

Mean probability difference: 0.7843283601959599
Maximum probability difference: 0.9999831331557908

## 8. ROC Curve
A combined ROC curve was produced. The visual comparison allowed the probability-based discrimination of the two models to be examined independently of the 0.5 classification threshold.

## 9. Statistical and Metric-Based Comparison

The available classification results show that the two models have identical performance when evaluated using the selected 0.5 threshold.
Both models:

- achieved 99.85% accuracy;
- correctly classified 1,997 of 2,000 observations;
- produced 1 false positive;
- produced 2 false negatives;
- produced identical precision values;
- produced identical recall values;
- produced identical F1-scores.

Therefore, the classification metrics alone do not distinguish the two models on this test set.
The probability-based measures provide an additional level of comparison. ROC-AUC will only be reported for both models once the probability calculations have been executed and are available for analysis.

## 10. Conclusion

Using a 0.5 classification threshold, the examination demonstrates that Random Forest and Logistic Regression produced identical hard-class predictions on the test set. As a result, their threshold-dependent classification metrics and confusion matrices are the same.
On the other hand, equal probability estimations do not follow from identical forecasts. 

Even if the models generate the same binary predictions, they could give the same observations different probabilities.Because of this, the final comparison takes into account both the probability-based ROC-AUC values and the threshold-dependent classification metrics. 
