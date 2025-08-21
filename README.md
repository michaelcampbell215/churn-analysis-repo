# Bank Customer Churn Predictive Model

## Project Overview

This project aims to predict whether a bank customer will churn (i.e., leave the bank) based on their historical data. By identifying customers at risk of churning, the bank can proactively engage with them through targeted marketing campaigns and retention offers to improve customer loyalty.

The analysis and model development are detailed in the `bank churn_predictive_model.ipynb` Jupyter Notebook.

---
# Dataset

The dataset used for this project is `Bank_churn_modelling.csv`. It contains 10,000 records of bank customers with the following attributes:

-   `RowNumber`: Row number
-   `CustomerId`: Unique identifier for each customer
-   `Surname`: Customer's last name
-   `CreditScore`: Customer's credit score
-   `Geography`: Customer's country (France, Spain, Germany)
-   `Gender`: Customer's gender
-   `Age`: Customer's age
-   `Tenure`: Number of years the customer has been with the bank
-   `Balance`: Customer's account balance
-   `NumOfProducts`: Number of bank products the customer uses
-   `HasCrCard`: Whether the customer has a credit card (1=Yes, 0=No)
-   `IsActiveMember`: Whether the customer is an active member (1=Yes, 0=No)
-   `EstimatedSalary`: Customer's estimated salary
-   `Exited`: Whether the customer churned (1=Yes, 0=No) - **This is the target variable.**

---

## Workflow

The project follows a structured machine learning workflow:

1.  **Data Loading & Initial Exploration:**
    *   The dataset is loaded into a pandas DataFrame.
    *   Initial checks are performed to understand the data's dimensions, data types, and look for missing values.

2.  **Exploratory Data Analysis (EDA):**
    *   **Univariate Analysis:** Distribution of key features like `CreditScore`, `Age`, `Balance`, and `Tenure` are visualized using histograms and box plots.
    *   **Bivariate Analysis:** The relationship between each feature and the target variable (`Exited`) is explored. Visualizations like count plots and bar charts are used to compare churn rates across different segments (e.g., by `Geography`, `Gender`, `HasCrCard`).
    *   **Correlation Analysis:** A heatmap is generated to identify multicollinearity between numerical features.

3.  **Data Preprocessing & Feature Engineering:**
    *   **Categorical Encoding:** Categorical features like `Geography` and `Gender` are converted into numerical format using one-hot encoding.
    *   **Feature Scaling:** Numerical features are scaled using `StandardScaler` to ensure that all features contribute equally to the model's training, preventing features with larger scales from dominating.
    *   **Train-Test Split:** The dataset is split into training (80%) and testing (20%) sets to prepare for model evaluation.

4.  **Model Building:**
    Several classification models were trained and evaluated to find the best performer:
    *   **Logistic Regression:** A baseline model to establish initial performance.
    *   **Random Forest Classifier:** An ensemble model known for its high accuracy and robustness.
    *   **XGBoost Classifier:** A gradient boosting model that is often a top performer in classification tasks.

5.  **Model Evaluation:**
    *   The models are evaluated on the unseen test set using a variety of metrics:
        *   **Accuracy:** Overall correct predictions.
        *   **Precision:** The proportion of positive identifications that was actually correct.
        *   **Recall (Sensitivity):** The proportion of actual positives that was identified correctly.
        *   **F1-Score:** The harmonic mean of Precision and Recall.
        *   **AUC-ROC Score:** A measure of the model's ability to distinguish between classes.
    *   A **Confusion Matrix** is also plotted for the best-performing model to visualize its performance in detail.

---

## Results

The models were compared based on their performance on the test data. The **XGBoost Classifier** emerged as the best-performing model, achieving the highest F1-Score and AUC-ROC score.

| Model | Accuracy | Precision | Recall | F1-Score | AUC-ROC |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Logistic Regression | 0.81 | 0.59 | 0.23 | 0.33 | 0.76 |
| Random Forest | 0.86 | 0.75 | 0.48 | 0.58 | 0.85 |
| **XGBoost Classifier** | **0.87** | **0.76** | **0.52** | **0.62** | **0.86** |

*Note: These results are representative and based on a typical run of the notebook.*

Key features influencing churn, as identified by the model, include `Age`, `NumOfProducts`, `Balance`, and `IsActiveMember`.
