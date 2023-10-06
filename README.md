# SVM-Model

## Overview

This project involves building and optimizing a Support Vector Machine (SVM) model for a classification task using a dataset. The dataset consists of several features related to employees, and the goal is to predict whether an employee will be "benched" (assigned to a non-billable project) or not.

## Dataset

The dataset is divided into two parts: `train_data.csv` and `test_data.csv`. The training data (`train_data.csv`) is used to train the SVM model, and the testing data (`test_data.csv`) is used to evaluate the model's performance.

### Features

The dataset contains the following features:

- `JoiningYear`: The year an employee joined the company.
- `PaymentTier`: Payment tier of the employee.
- `Age`: Age of the employee.
- `ExperienceInCurrentDomain`: Experience of the employee in the current domain.
- `Education_Bachelors`: Binary feature indicating if the employee has a bachelor's degree.
- `Education_Masters`: Binary feature indicating if the employee has a master's degree.
- `Education_PHD`: Binary feature indicating if the employee has a Ph.D.
- `City_Bangalore`: Binary feature indicating if the employee is located in Bangalore.
- `City_New Delhi`: Binary feature indicating if the employee is located in New Delhi.
- `City_Pune`: Binary feature indicating if the employee is located in Pune.
- `Gender_Male`: Binary feature indicating if the employee is male.
- `EverBenched_Yes`: Binary feature indicating if the employee has ever been benched.

### Target

The target variable is `Target`, which is binary (0 or 1) and represents whether an employee is benched (1) or not (0).

## Model Building and Evaluation

### Baseline SVM

A baseline SVM model is built with the following configuration:

- Kernel: Linear
- Regularization parameter (C): 1
- Class weights: Balanced

The model is trained on the training data, and the following evaluation metrics are computed:

- Accuracy
- Recall
- AUC score
- Precision
- Confusion Matrix
- F1 Score

The baseline SVM model achieves the following results:

- Accuracy: 0.7186
- Recall: 0.675
- AUC score: 0.7082
- Precision: 0.5775
- Confusion Matrix:
  ```
  [[453 158]
  [104 216]]
  ```
- F1 Score: 0.6225

### Model Optimization with GridSearchCV

GridSearchCV is used to optimize the SVM model by searching for the best hyperparameters. The following hyperparameters are considered:

- Kernel: Linear, Polynomial, Radial basis function (RBF)
- Regularization parameter (C): 1, 2, 3, 4, 5
- Gamma: 0.1, 0.3, 0.5, 0.7, 1, 1.2, 1.4, 1.6, 1.8, 2.0
- Class weights: Balanced

The best hyperparameters for the optimized model are:

- Kernel: RBF
- C: 4
- Gamma: 1
- Class weights: Balanced

The optimized model achieves the following results:

- Accuracy: 0.8550
- Recall: 0.7625
- AUC score: 0.8330
- Precision: 0.8053
- Confusion Matrix:
  ```
  [[552  59]
  [ 76 244]]
  ```
- F1 Score: 0.7833

### Feature Selection Based on Correlation

Feature selection is performed based on the correlation between features and the target variable. Features with low correlation (less than 0.01) with the target variable are removed. The following features are removed:

- Age
- Experience in Current Domain
- Education PHD
- City New Delhi
- Ever Benched Yes

### Model Optimization with GridSearchCV (Features Removed)

GridSearchCV is used again to optimize the SVM model after removing the low-correlation features. The same hyperparameters as before are considered.

The best hyperparameters for the optimized model with features removed are the same as before:

- Kernel: RBF
- C: 4
- Gamma: 1
- Class weights: Balanced

The optimized model with features removed achieves the following results:

- Accuracy: 0.8238
- Recall: 0.7656
- AUC score: 0.8100
- Precision: 0.7335
- Confusion Matrix:
  ```
  [[522  89]
  [ 75 245]]
  ```
- F1 Score: 0.7833

## Conclusion

In this project, a Support Vector Machine (SVM) model was built and optimized for a classification task using a dataset of employee data. Feature selection based on correlation with the target variable was
