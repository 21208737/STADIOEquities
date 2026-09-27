# Data Preprocessing

The Bank Customer Churn Dataset, which has about 10,000 customer records, was chosen. Where Exited is the target variable, with 0 indicating a customer who has been retained and 1 indicating a customer who has left or churned. There is one target variable and thirteen predictor variables in the dataset.

# Preprocessing steps

## The following steps will be implemented in 01_Preprocessing.ipynb:
1. Import the required Python libraries.
2. Load the Bank Customer Churn dataset.
3. Inspect the dataset structure and data types.
4. Identify missing values and duplicate records.
5. Remove variables that are identifiers rather than meaningful predictors: RowNumber, CustomerId and Surname.
6. Separate the predictors from the target variable Exited.
7. Encode categorical variables: Geography and Gender.
8. Separate numerical and categorical features.
9. Split the dataset into Training and Testing sets using an 80:20 stratified split.
9. Apply feature scaling.
10. Apply SMOTE only to the Training data to avoid information leakage.
11. Retain the original class distribution in the Test Set.
