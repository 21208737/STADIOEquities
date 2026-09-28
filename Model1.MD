# Model 1 – Logistic Regression

## 1. Model Overview

Model 1 uses **Logistic Regression** to predict customer churn using the Bank Customer Churn Dataset.

The target variable is `Exited`:

- `0` = customer retained
- `1` = customer exited/churned

Logistic Regression was selected as Model 1 because it is a supervised classification model used in the banking customer-churn.

## 2. Related Notebook

The implementation of Model 1 is contained in:

https://github.com/21208737/STADIOEquities/blob/49cd2c3f4390b75f6bf71eed548aec2145fe4f45/experimental-setup/notebooks/03_Model1.ipynb

To run the model, open the notebook in JupyterLab and execute the cells sequentially.

## 3. Data Preprocessing

The following preprocessing steps are applied:

- 'RowNumber', 'CustomerId' and 'Surname' are removed.
- 'Exited' is separated as the target variable.
- 'Geography' and `Gender` are one-hot encoded.
- The dataset is divided into training and testing sets using a stratified 80:20 split.
- Numerical features are scaled before Logistic Regression is trained.
- SMOTE is applied **only to the training data** to address class imbalance.

## 4. Feature Engineering

The model uses engineered variables based on the approach discussed in the literature review, including:

- 'AgeGroup'
- 'Engaged'
- 'Tenure_Age_Ratio'
- 'Balance_Salary_Ratio'
- 'ZeroBalance'

These features provide additional information that may assist in identifying customer churn patterns.

## 5. Logistic Regression Model

The Logistic Regression classifier is trained using the prepared and scaled training data.

The model uses:


LogisticRegression(
    max_iter=1000,
    random_state=42
)

The parameters investigated include:

C
solver
class_weight

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

The detailed Model 1 results are documented separately in:

Model1Performance.MD

## 7. How to Run

- Ensure the required packages in requirements.txt are installed.
- Ensure the Bank Customer Churn Dataset is available in the project dataset folder.

Open:
https://github.com/21208737/STADIOEquities/blob/49cd2c3f4390b75f6bf71eed548aec2145fe4f45/experimental-setup/notebooks/03_Model1.ipynb

Run the notebook cells sequentially.
Review the generated predictions and model outputs.
