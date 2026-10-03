# Predicting Diabetes Using BRFSS Data

## Overview

This project uses data from the Behavioral Risk Factor Surveillance System (BRFSS) to explore whether selected demographic, behavioral, and health related variables can be used to predict diabetes.

The analysis focuses on preparing a large public health dataset and comparing three classification models: Decision Tree, Random Forest, and XGBoost.

The project also examines missing data, potential data leakage, class imbalance, and model performance using several evaluation metrics.

## Research Question

Can demographic, behavioral, and health related variables from the BRFSS dataset be used to predict diabetes?

## Dataset

The Behavioral Risk Factor Surveillance System (BRFSS) is a large US health survey that collects information about health related behaviors, chronic health conditions, and preventive practices.

The analysis used 457,670 observations and selected variables related to:

- Age
- Sex
- Education
- Income
- Exercise
- Smoking
- Alcohol consumption
- BMI
- Employment
- Physical health
- Cardiovascular conditions
- Food insecurity

The target variable was `DIABETE4`, which was converted into a binary classification variable.

The original BRFSS dataset is not included in this repository.

## Methodology

The project followed these main steps:

1. Data inspection and variable selection
2. Data cleaning and recoding
3. Missing data analysis
4. Train and test split
5. Imputation of missing values
6. Classification model development
7. Model evaluation
8. Interpretation of results and limitations

## Data Preparation

The dataset contained several coded values representing responses such as "Don't know," "Refused," and missing responses. These values were converted to missing values before modeling.

Alcohol consumption was also standardized from the original BRFSS coding into days of alcohol consumption per month.

The target variable was converted into a binary outcome.

To reduce the risk of data leakage, the data was divided into training and testing sets before imputation. Missing values were then handled separately within the appropriate datasets.

## Missing Data

Missingness was present across several variables, with the highest proportion occurring in `SDHFOOD1`.

The high missingness in this variable was related to the fact that the Social Determinants of Health module was not implemented by every state.

Little's MCAR test produced a p-value below 0.001, indicating that the missing data did not appear to be Missing Completely At Random.

Because the dataset suggested a more complex missing data mechanism, several approaches were considered. The final analysis used median imputation for numerical variables and mode imputation for categorical variables, while observations with missing target values were removed.

## Outliers

Boxplots, skewness, and the IQR method were used to examine potential outliers in variables such as alcohol consumption and BMI.

Although several extreme observations were identified, they were not removed because the dataset represents health conditions and behaviors where extreme values may represent real observations.

## Modeling

Three classification models were compared:

- Decision Tree
- Random Forest
- XGBoost

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1 score
- ROC AUC
- Confusion matrix
- ROC curve

Because the target variable was imbalanced, accuracy alone was not considered sufficient for evaluating model performance.

Recall was also examined because false negatives can be particularly important in a health related prediction context.

## Model Performance

| Model | ROC AUC | Accuracy | Recall |
|---|---:|---:|---:|
| Decision Tree | 0.74 | 0.86 | 0.06 |
| Random Forest | 0.75 | 0.85 | 0.12 |
| XGBoost | 0.79 | 0.86 | 0.08 |

XGBoost produced the highest ROC AUC among the three models. Random Forest produced the highest recall, although recall remained relatively low across all three models.

## Results

The models produced moderate ROC AUC and accuracy values, but recall was low across all three approaches.

The results demonstrate that achieving reasonable overall classification performance does not necessarily mean that a model is suitable for identifying most positive diabetes cases.

The analysis also highlighted the importance of data preparation, particularly when working with a large public health dataset containing coded responses, missing values, imbalanced outcomes, and potentially influential variables.

The Decision Tree provided an additional way to examine relationships between variables. Age was the main predictor in the first levels of the tree, followed by BMI, with alcohol consumption also appearing as an important variable.

## Limitations

Several limitations should be considered:

- The dataset contains substantial missingness in some variables.
- The missing data mechanism may not be completely random.
- The target variable is imbalanced.
- Recall remained low for all three models.
- The analysis does not establish causal relationships between the predictors and diabetes.
- The models should not be considered suitable for clinical diagnostic use based on these results.

## Key Takeaways

This project demonstrates a complete classification workflow using a large public health dataset, from data preparation and missing data analysis to model comparison and interpretation.

A key finding was that model performance depends on the evaluation metric being considered. While the models achieved similar accuracy and moderate ROC AUC values, their recall was substantially lower.

The project also reinforced the importance of avoiding data leakage and considering the practical meaning of model errors when working with health related data.

## Tools

- Python
- pandas
- NumPy
- scikit-learn
- XGBoost
- Matplotlib
- Seaborn

## Project Type

Individual academic project

## Author

Kleber Moran