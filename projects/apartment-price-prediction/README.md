
# Apartment Price Prediction

## Overview

This project explores machine learning models for predicting apartment prices from property characteristics.

The original problem is a **regression task**, where the objective is to predict the numerical value of `last_price`. For learning and model comparison purposes, the dataset was also transformed into a **binary classification problem**, separating apartments into low- and high-price categories.

The project covers data exploration, data preparation, classification, regression, hyperparameter selection, model evaluation, and feature importance analysis.

## Objectives

- Explore and prepare an apartment price dataset for machine learning.
- Transform the original price variable into a binary classification target.
- Train and compare different classification models.
- Train and compare different regression models.
- Select model hyperparameters using a validation set.
- Evaluate model performance using appropriate metrics.
- Analyze the importance of the features used by the final regression model.
- Document the results and conclusions in a reproducible Jupyter Notebook.

## Dataset

The dataset contains **6,495 apartment listings** and initially included 14 variables describing apartment characteristics, location, and price.

The original target variable is:

- `last_price` — apartment price.

Two constant variables, `studio` and `open_plan`, were removed during data preparation because they contained only a single unique value.

For classification, `last_price` was transformed into the binary variable `price_class` using the median price of **$113,000** as the threshold:

- `0` — price ≤ $113,000
- `1` — price > $113,000

The two classes are approximately balanced, containing 3,258 and 3,237 observations respectively.

The original dataset is not included in the repository. It is kept locally and excluded through `.gitignore`.

## Methodology

### 1. Data Exploration

The dataset was inspected using descriptive statistics and visualizations.

The analysis included:

- Dataset dimensions and data types.
- Descriptive statistics.
- Price distribution.
- Distribution of prices below $500,000.
- Relationship between total apartment area and price.
- Review of the main numerical variables.
- Identification of constant features.

The exploratory analysis showed a strong positive relationship between apartment area and price, although the dataset contains substantial variability and several high-price outliers.

### 2. Classification

The classification task predicts whether an apartment belongs to the lower- or higher-price category.

The features were separated from the target, with `last_price` excluded from the predictors to prevent **data leakage**, since `price_class` is directly derived from `last_price`.

The dataset was divided into:

- 75% training data
- 25% validation data

Three models were evaluated:

- Decision Tree Classifier
- Random Forest Classifier
- Logistic Regression

The evaluation metric was **accuracy**.

#### Classification Results

| Model | Training Accuracy | Validation Accuracy |
|---|---:|---:|
| Decision Tree | 87.66% | 87.25% |
| Random Forest | 100.00% | **90.39%** |
| Logistic Regression | 88.11% | 88.24% |

The best validation performance was obtained by the **Random Forest Classifier with 70 trees**, achieving an accuracy of approximately **90.39%**.

A second experiment tuned both `n_estimators` and `max_depth`. Although the tuned model reduced the gap between training and validation performance, its validation accuracy was slightly lower than the best 70-tree model.

### 3. Regression

The regression task predicts the original numerical apartment price.

The target variable was scaled by dividing `last_price` by 100,000 during modeling. Results were converted back to the original price scale when interpreting the model.

The same 75/25 train-validation split was used.

Four approaches were compared:

- Mean-price baseline
- Decision Tree Regressor
- Random Forest Regressor
- Linear Regression

The evaluation metric was **Root Mean Squared Error (RMSE)**.

A lower RMSE indicates better predictive performance.

#### Regression Results

| Model | Validation RMSE | Approx. Error |
|---|---:|---:|
| Baseline | 2.6528 | $265,282 |
| Decision Tree | **1.2493** | **$124,929** |
| Random Forest | 1.4531 | $145,309 |
| Linear Regression | 1.5452 | $154,520 |

The best regression model was a **Decision Tree Regressor with `max_depth=8`**.

Its validation RMSE was approximately **1.2493**, corresponding to an RMSE of approximately **$124,929** in the original price scale.

Additional tree depths from 11 to 20 were tested, but none improved upon the validation result obtained with `max_depth=8`.

## Feature Importance

Feature importance was analyzed using the final Decision Tree Regressor.

The most influential features were:

| Feature | Importance |
|---|---:|
| `total_area` | 71.12% |
| `kitchen_area` | 15.74% |
| `cityCenters_nearest` | 4.66% |
| `ceiling_height` | 2.84% |
| `airports_nearest` | 2.03% |

`total_area` was by far the most influential feature in the final model.

Feature importance indicates how much the trained decision tree relied on each variable for its predictions; it should **not be interpreted as evidence of causation**.

## Predictions vs. Actual Prices

The final regression model was evaluated on the validation set by comparing predicted prices with their actual values.

The resulting scatter plot shows a general positive relationship between actual and predicted prices. However, the model has greater difficulty with some high-priced apartments and extreme observations.

For example, an apartment with an actual price of approximately **$1.82 million** was predicted at approximately **$1.52 million**, producing an error of about **$303,130**.

This behavior is particularly relevant because RMSE gives greater weight to large prediction errors.

## Conclusions

The experiments demonstrate that different machine learning models perform differently depending on the task.

For classification, the **Random Forest Classifier** achieved the best validation accuracy at approximately **90.39%**.

For regression, the **Decision Tree Regressor with `max_depth=8`** performed best, achieving a validation RMSE of approximately **$124,929** and substantially improving upon the mean-price baseline.

The feature importance analysis showed that `total_area` was the dominant feature used by the final regression model, followed by `kitchen_area` and `cityCenters_nearest`.

The results also demonstrate the importance of evaluating models on unseen validation data. Although the final decision tree was retrained using the complete dataset after model selection, its reported performance is based on the earlier validation experiment rather than its training error.

Overall, this project provided practical experience with **classification, regression, model comparison, hyperparameter selection, evaluation metrics, feature importance, and data leakage prevention** using scikit-learn.

## Technologies

- Python
- pandas
- NumPy
- scikit-learn
- Matplotlib
- Jupyter Notebook
- Git
- GitHub

## Project Structure

```text
apartment-price-prediction/
├── README.md
├── .gitignore
├── notebook/
│   └── apartment_price_prediction.ipynb
├── results/
│   ├── classification_results.csv
│   ├── regression_results.csv
│   └── feature_importance.csv
├── data/
│   └── README.md
└── src/
