# Overfitting vs Underfitting
`data science` `scikit-learn` </br>
</br>
![over under ex](https://github.com/user-attachments/assets/43f0131a-18d3-47ec-8a29-bd93cd116473)

## What is Overfitting?
Overfitting is when a model fits too well, or exactly, with the training data. When this happens, a model will not be able to 
make accurate predictions off any testing data or any data it has never seen before.

## How Does Overfitting Happen?
Some causes of overfitting include:
* Too complex of a model (too many parameters)
  * A complex model picks up noise or outliers (irrelevant info) within the training data
  * Deep neural networks or high-degree polynomials
* Not enough training data
  * Small datasets may not provide your model with enough information
* Model performs exceptionally well to your training data
  * Most likely will perform poorly off your test data
  * Does not generalize well with unseen data

## How to Prevent Overfitting
* Scikit-learn's `train_test_split`
  * Model can be trained until performance is good for both the training and testing data
* Cross-validation
  * Evaluate model performance more reliably by training and testing it on multiple splits of the data
  * Beneficial to prevent underfitting as well
* Larger dataset to train and test on
* Feature selection
  * Remove irrelevant features and keep important features
  * Run the baseline with all features then test this against a model trained without a feature to see if the performance improves
* L1 / L2 regularization
  * Constrain our data to prevent too complex of a model
* Lasso regularization


---
## What is Underfitting?
Underfitting is when a model is too simple and cannot capture the underlying patterns in the data. This model will perform poorly
with any data, whether its training or testing data.

## How Does Underfitting Happen?
Some causes of underfitting include:
* Too simple of a model
  * ex: using a linear regression model for non-linear data
* Too much regularization
  * Penalizing the model too heavily
* Important features missing from the data
* Poor performance with training and testing data (high bias, low variance)

## How to Prevent Underfitting?
* Cross-validation
* Feature selection
* Tune hyperparameters
  * Scikit-learn's `GridSearchCV` - tries all combinations of parameters in a grid (can be slow)
  * Scikit-learn's `RandomizedSearchCV` - random subset of parameters (not guranteed to find best)

