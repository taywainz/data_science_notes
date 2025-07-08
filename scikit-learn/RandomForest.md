# RandomForests
`python` `scikit-learn`

## What is RandomForestClassifier
`RandomForestClassifier` is an algorithm that uses multiple decision trees (ensemble learning) to _classify data_. It combines 
the outputs of thesedecision trees to produce a final _classification_ output (discrete labels). This approach helps improve 
accuracy and reduce overfitting compared to a single decision tree.</br>
</br>
Check out the most up-to-date information about hyperparameters [here](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)

![rf](https://github.com/user-attachments/assets/dd1dd53c-10a4-4205-bce3-9947c3684e93)

## What is RandomForestRegressor
Very similar to its counterpart, `RandomForestRegressor` is used to make predictions on _continuous_ numerical data like
predicting house prices or stock prices.

## When to Use RandomForests
RandomForests should be used:
* On classification or regression tasks
* When you do not care if a feature has a positive or negative relationship with the target
  * Logistic Regression or Lasso are better choices
* Feature selection
  * If you fit the algorithm with features that are not useful, the algorithm simpy won't use them to split on the data
* When you do not have testing data that is outside the bounds of your original data
  * Ex: if you want to predict how much a 10 bedroom house costs but have only trained your data on houses with a max bedroom of 4 and max price of $700,000 then your model would predict the 10 bedroom house as $700,000 (the max cost during training). A different linear regression model would be better in this situation.

## Benefits of RandomForests
Some benefits include:
* Improves accuracy
* Reduces overfitting
* Can be used on large datasets
* Works with numerical and categorical features
  * No issues when features are different types or different ranges compared to other methods (like linear or logistic regression)
* Less influenced by outliers and noise
* Can estimate feature importance

## Key Points
`RandomForestClassifier` or `RandomForestRegressor` are great models to initially test your data on. Majority of the time,
the RandomForest model will provide good performance. If it does not, it is better to explore other models.</br>
</br>
Want to predict a category or label? - `RandomForestClassifier`</br>
Want to predict a number or quantity? - `RandomForestRegressor`

