1. Problem Statement:
The objective of this project is to predict the efficiency of solar panels based on various environmental, installation, and operational features.


2. Tools and Technologies Used:

Languages: Python
Libraries:
 pandas, numpy (Data Handling)
 seaborn, matplotlib (EDA & Visualization)
 scikit-learn (Preprocessing & Modeling)
Environment: Google Colab Notebook


3. Data Preprocessing:

Invalid Entry Handling:
  Replaced 'unknown', 'badval', 'UNK' in object-type numeric columns (`humidity`, `wind_speed`, `pressure`) with `NaN` and converted to numeric.

Missing Value Imputation:

   Numeric columns: filled with median
   Categorical columns: filled with mode

 Dropped Uncorrelated Features:
  Based on the correlation heatmap, removed columns with low correlation to the target:

  ['humidity', 'temperature', 'maintenance_count', 'cloud_coverage', 'wind_speed', 'pressure']

 Outlier Handling:
  Evaluated using boxplots but didn't explicitly remove any rows to preserve dataset size and avoid data loss.

 Encoding:

   One-hot encoded categorical variables:
    `string_id`, `error_code`, `installation_type` using `pd.get_dummies()`
   Used `drop_first=True` to avoid multicollinearity.

 Test Data Alignment:

   Encoded test data similarly.
   Used `reindex(columns=train_columns, fill_value=0)` to align with training features.


4. Feature Selection:

 Removed `id` column from the feature set.
 Defined target variable as `efficiency`.
 Final training feature set: 13 features.


5. Modeling:

 Evaluated multiple regression models:

   Linear Regression
   Random Forest Regressor
   Gradient Boosting Regressor

 Best Model:
  Gradient Boosting Regressor

   RMSE: 0.1064
   R² Score: 0.4364


6. Submission File:
 Format:
  id, efficiency
 
 Predictions were generated using the Gradient Boosting model on the encoded test set.


7. Summary:

A robust data pipeline was created involving:

 Data cleaning and imputation,
 Feature reduction based on correlation,
 Encoding for model compatibility,
 Consistent feature alignment between train and test,
 Modeling with multiple algorithms and evaluation via RMSE and R².

This approach ensures that both model accuracy and data integrity are preserved.