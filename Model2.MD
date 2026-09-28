# Model 2 – Random Forest

## 1. Model Overview

Model 2 uses a **Random Forest Classifier** to predict customer churn using the Bank Customer Churn Dataset.

The target variable is 'Exited':

- '0' = customer retained
- '1' = customer exited/churned

Random Forest was selected as Model 2 because it is a supervised classification model used in the banking customer-churn.

## 2. Related Notebook

The implementation of Model 2 is contained in:

'notebooks/04_Model2.ipynb'

To run the model, open the notebook in JupyterLab and execute the cells sequentially.

## 3. Data Preprocessing

The following preprocessing steps are applied:

- 'RowNumber', 'CustomerId' and 'Surname' are removed.
- 'Exited' is separated as the target variable.
- 'Geography' and 'Gender' are one-hot encoded.
- The dataset is divided into training and testing sets using a stratified 80:20 split.
- SMOTE is applied **only to the training data** to address class imbalance.

## 4. Feature Engineering

The model uses engineered variables based on the approach discussed in the literature review, including:

- 'AgeGroup'
- 'Engaged'
- 'Tenure_Age_Ratio'
- 'Balance_Salary_Ratio'
- 'ZeroBalance'

These variables are intended to provide additional information about customer characteristics and behaviour.

## 5. Random Forest Model

The Random Forest classifier is trained using the prepared training data.

The model configuration includes:


RandomForestClassifier(
    random_state=42
)

The parameters investigated include:

- n_estimators
- max_depth
- min_samples_split
- min_samples_leaf

## 6. Model Output

The notebook generates:

- Customer class predictions
- Customer churn probabilities
- Confusion matrix
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

The detailed results are documented separately in:
Model2Performance.MD

## 7. How to Run

-Ensure the required packages in requirements.txt are installed.
-Ensure the Bank Customer Churn Dataset is available in the project dataset folder.

Open:
notebooks/04_Model2.ipynb

Run the notebook cells sequentially.
Review the generated predictions and model outputs.
