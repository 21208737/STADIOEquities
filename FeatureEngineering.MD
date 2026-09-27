# Feature Engineering

Binary variables were binary encoded, categorical variables were numerically encoded, and unordered categories were one-hot encoded. Five engineering variables were created as well: AgeGroup, Engaged, Tenure_Age_Ratio, Balance_Salary_Ratio, and ZeroBalance. Continuous variables were standardised for models that were sensitive to distance. Before applying SMOTE the training data, the dataset was split to address class imbalance; the test set retained its original distribution.
