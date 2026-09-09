# Apartment Price Prediction

## Overview

This project explores machine learning models for apartment price prediction.

The original problem is a **regression task**, since the target variable (`last_price`) is a numerical value. For learning and comparison purposes, the problem is also transformed into a **binary classification task**, where apartments are divided into low- and high-price categories.

## Objectives

The project aims to:

* Prepare the apartment dataset for machine learning.
* Build a binary classification problem from apartment prices.
* Train and compare different classification models.
* Build regression models to predict apartment prices.
* Evaluate models using appropriate metrics.
* Tune selected hyperparameters using a validation set.
* Select the best-performing model.
* Train the final model using the complete dataset.

## Models

### Classification

* Decision Tree Classifier
* Random Forest Classifier
* Logistic Regression

**Metric:** Accuracy

### Regression

* Decision Tree Regressor
* Random Forest Regressor
* Linear Regression

**Metric:** Root Mean Squared Error (RMSE)

## Dataset

The project uses an apartment listing dataset containing information about apartment characteristics and their prices.

The original target variable is:

`last_price`

For the classification task, prices are transformed into two classes using the median price of **$113,000**:

* `0` — price ≤ $113,000
* `1` — price > $113,000

The original dataset is not included in this repository.

## Technologies

* Python
* pandas
* scikit-learn
* Jupyter Notebook
* Git
* GitHub

## Project Structure

```text
apartment-price-prediction/
├── README.md
├── notebook/
├── src/
├── results/
└── data/
    └── README.md
```

## Status

🚧 In progress
