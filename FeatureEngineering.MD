# Feature Engineering

## 1. Overview

Feature engineering is used to create additional variables that may provide useful information for predicting customer churn. Binary variables were binary encoded, categorical variables were numerically encoded, and unordered categories were one-hot encoded. Five engineering variables were created as well: AgeGroup, Engaged, Tenure_Age_Ratio, Balance_Salary_Ratio, and ZeroBalance. Continuous variables were standardised for models that were sensitive to distance. Before applying SMOTE the training data, the dataset was split to address class imbalance; the test set retained its original distribution.

The feature engineering approach is informed by the banking customer-churn.

## 2. Related Notebook

The feature engineering process is contained in:

https://github.com/21208737/STADIOEquities/blob/5e52ef4533792c7a07f4e13e37644c8d4d034fc6/experimental-setup/notebooks/02_FeatureEngineering.ipynb

To run the process, open the notebook in JupyterLab and execute the cells sequentially.

## 3. Engineered Features

The following features are created:

| Feature | Description |
|---|---|
| 'AgeGroup' | Groups customers according to age |
| 'Engaged' | Represents the customer's active-member status |
| 'Tenure_Age_Ratio' | Ratio between customer tenure and age |
| 'Balance_Salary_Ratio' | Ratio between account balance and estimated salary |
| 'ZeroBalance' | Indicates whether the customer's balance is zero |

Example:


df["Engaged"] = df["IsActiveMember"]

df["Tenure_Age_Ratio"] = (
    df["Tenure"] /
    df["Age"].replace(0, np.nan)
)

df["Balance_Salary_Ratio"] = (
    df["Balance"] /
    df["EstimatedSalary"].replace(0, np.nan)
)

df["ZeroBalance"] = (
    df["Balance"] == 0
).astype(int)

## 4. Age Group

Customers are grouped into age categories:

def create_age_group(age):
    if age < 30:
        return "Young"
    elif age < 45:
        return "Middle"
    elif age < 60:
        return "Mature"
    else:
        return "Senior"

df["AgeGroup"] = df["Age"].apply(create_age_group)

The specific age-group boundaries are project modelling decisions.

## 5. Output

The notebook produces a dataset containing the original relevant predictors together with the engineered features.
The resulting data is used by the Model 1 and Model 2 notebooks.

## 6. How to Run

- Ensure the required packages in requirements.txt are installed.
- Ensure the Bank Customer Churn Dataset is available.

Open:
https://github.com/21208737/STADIOEquities/blob/5e52ef4533792c7a07f4e13e37644c8d4d034fc6/experimental-setup/notebooks/02_FeatureEngineering.ipynb

Run the notebook cells sequentially.
Use the resulting engineered dataset for the modelling notebooks
