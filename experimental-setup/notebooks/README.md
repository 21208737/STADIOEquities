## SS3 Part B: Final Model Decision

# Project objective

This project applies the Random Forest classification method selected in SS2 to STADIOEquities client data. The business objective is to identify, at an early stage, whether a newly registered client is likely
to activate their investment account. This can help STADIOEquities prioritise onboarding support and encourage clients to make their first deposit.

The target variable, activation_outcome, False represents not activated and True represents activated.

# Data used

The notebook reads nine CSV extracts supplied in stadioequities.zip, including client-account, app/web behaviour, funding, trading, product
subscription, support feedback, marketing, compliance, and modelling-outcome data.

The extracts were consolidated at client level using client_id. The resulting dataset contains 2,104 clients and 120 columns, with one unique row per client and no missing activation labels.

  | Activation class | Clients |  Percentage |
  | ---------------- | ------- | ----------- |
  | Not activated (False) | 1,288 | 61.22% |   
  | Activated (True) | 816 | 38.78% |
  | Total | 2,104 | 100% |

The target has a majority-to-minority ratio of approximately 1.58:1. This is a moderate class imbalance, so the notebook uses stratified
splitting and a class-weighted Random Forest.

# Preprocessing and evaluation approach

The dataset was divided into 70% training (1,472 clients), 15% validation (316), and 15% unseen test data (316). Stratification preserved similar activation proportions across the subsets.

The npreprocessing pipeline: - removes client identifiers and
target/outcome fields that should not be model inputs; - derives
registration date features and days between registration and KYC where
appropriate; - imputes missing numeric values with the median and
categorical values with the most frequent value; - one-hot encodes
categorical variables, safely handling categories not seen during
training; and - fits preprocessing on the training subset to reduce data
leakage.

A leakage review found that many operational activity variables and
post-registration timestamps could reveal behaviour occurring after the
intended prediction point. The notebook therefore removed 90 potentially
leaking columns, leaving 10 candidate predictors: kyc_status,
acquisition_channel, region, age, stated_goal, risk_appetite,
registration_year, registration_month, registration_dayofweek, and
days_registration_to_kyc.

# Final decision: retain Random Forest as the selected method, with leakage controls

The final method remains Random Forest, consistent with the choice
made in SS2. It is suitable for this classification task because it can
model non-linear relationships and interactions between client
characteristics, can work with a mixture of numeric and categorical
predictors after preprocessing, and provides feature-importance
diagnostics.

It uses 300 trees, min_samples_leaf=2,
class_weight="balanced", random_state=42, and n_jobs=-1. The
maximum tree depth is unrestricted (max_depth=None). The balanced
class weighting is intended to account for the difference in class
frequencies.

The decision is based on the clean retrained model, not the initial
results. The initial model reported perfect validation and test scores,
but the leakage review showed that many predictors were recorded after
registration or were strongly associated with the outcome. Those perfect
scores should therefore not be treated as credible evidence of
real-world performance.
Clean model results

  | Metric | Validation | Unseen test |
  | -------| ---------- | ----------- |
  | Accuracy | 80.70%   |     81.65%. |
  | Precision for activated clients| 67.03% | 68.18% |
  | Recall for activated clients | 99.19%     | 98.36% |
  | F1-score for activated clients | 80.00%   | 80.54% |
  | ROC-AUC                        | 0.8777   | 0.8531 |

The clean model's validation and test results are reasonably close,
which is encouraging. On the unseen test set, it correctly identifies
most activated clients (high recall), but its precision for the
activated class is lower. This means a substantial number of clients
predicted as activated may actually be non-activated. The model should
therefore be treated as a useful baseline rather than a production-ready
decision-maker.

# Business interpretation

The model could support onboarding teams by helping them understand
which registered clients may need additional engagement. However, this
notebook predicts the activation outcome, not dormancy directly. It
should not be described as a validated dormancy prediction model.

Before operational use, STADIOEquities should define a prediction cut-off (for example, immediately after registration or after KYC completion) and ensure every feature would genuinely be available by
that point. The days_registration_to_kyc feature is only appropriate if KYC completion has already occurred by the chosen prediction time. Features that depend on future funding, trading, support, marketing responses, or other post-cut-off events must not be included.

# Conclusion

Random Forest is retained as the final method because it aligns with the SS2 decision and achieves an unseen-test accuracy of 81.65% and ROC-AUC of 0.8531 after a leakage
review. The clean results are more credible than the initial perfect scores, but further feature-timing checks, threshold selection, and
validation on future client cohorts are necessary before real-world deployment.
