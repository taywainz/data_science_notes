# Machine Learning Train Test Split
`python` `scikit-learn`

## What is Train Test Split?
`train_test_split` is used in machine learning to randomly split your dataset into a training set and a test set. The training set
is used to train your model, while the test set acts as *new* data to test your model's accuracy and performance.</br>
</br>
Typically 80% of the data is allocated to the training set while 20% of the data is for the test set.

## Benefits
* Evaluate your model's performance on unseen data - also known as `generalization`
* Prevents `overfitting`. This is when a model is trained too well on the training data that most likely contains noise and outliers
  * A model with high accuracy on the training data but a poor accuracy on the test data
  * A model that is too complex that captures patterns that don't generalize
* Simulates real-world scenarios where your model will be making predictions off data it has never seen before
* Can use stratified sampling for classification problems where classes are imbalanced
  * Ensures the proportions in your train and test sets are equal with your original dataset

## Example
First, you must examine your dataset and determine what the *target* attribute is, and what *features* you will use. The *target*
is depicted as `y` while the *features* are depicted as `X`. Once they are identified, you can split your data.</br>
</br>
In this example, we want to predict the price of a house. Price will be our *target*.
> ```python
> import pandas as pd
> from sklearn.model_seection import train_test_split
>
> df = pd.read_csv('random_data_ex.csv')
>
> y = df['price']
> X = df.drop(['price'])
>
> X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2) 
> ```

>[!NOTE]
> If you want stratified splits, insert `stratify=y` within the `train_test_split`

