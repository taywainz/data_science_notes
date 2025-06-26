# Machine Learning Pipelines
`python` `scikit-learn`

## What Are Pipelines
Pipelines are commonly used in machine learning. They allow you to organize your processing steps to ensure your steps are executed
in the correct order to ensure consistency and reproducibility.</br>
</br>
Some benefits of pipelines:
* Helps prevent data leakage
* Organization encapsulates cleaner code and ensures same steps executed in the same order
* Once created, can use to run entire sequence of steps repeatedly with new data

## When to Use Pipelines
After identifying and splitting your features and target attribute (`X` and `y`), you will need to determine what features 
you will want to use in your model. This limits your data which is beneficial for reducingcomplexity and improve model 
performance by focusing on the most relevant features.</br>
</br>
These selected columns need to be categorized as numerical, categorical, or ordinal. Once classified, you will know what type of
pipeline(s) you need to create for your data.

## What Can Be Included in Pipelines
Pipelines can contain the following processes:
* Data Cleaning (handle missing values or removing duplicates)
* Feature engineering (custom transformers)
* Training your model
* Evaluating metrics like precision, recall, accuracy, F1 score
* Predicting outcome of unseen data using your trained model

However, processes in your pipeline depend on what type of data you are analyzing.</br>
</br>
**Numeric Pipeline**
* Custom transformer
* SimpleImputer(strategy='median') or 'mean'
* StandardScaler

**Categorical Pipeline**
* Custom transformer
* SimpleImputer(strategy='most_frequent')
* OneHotEncoder

**Ordinal Pipeline**
* Custom transformer
* SimpleImputer(strategy='most_frequent')
* OrdinalEncoder

## Example
Here is an example of what these pipelines may look like in Python using the `make_pipeline` and `Pipeline` methods.
> ```python
> from sklearn.pipeline import Pipeline, make_pipeline
> from sklearn.impute import SimpleImputer
> from sklearn.preprocessing import StandardScaler, OneHotEncoder, Ordinal Encoder
>
> num_pipeline = make_pipeline(
>     SimpleImputer(strategy='median'),
>     StandardScaler())
>
> cat_pipeline = make_pipeline(
>     SimpleImputer(strategy='most_frequent'),
>     OneHotEncoder())
>
> ord_pipeline = Pipeline([('impute', SimpleImputer(strategy='most_frequent')),
>                          ('ordinal-encoder', OrdinalEncoder())])
> ```

## Additional Information
Typically after creating a pipeline, you will use this pipeline within a column transformer. This is especially crucial
if you have multiple pipelines due to the different data types. This ensures the preprocessing steps are applied to the
correct columns and in the correct order.</br>
Example using `ColumnTransformer`
> ```python
> from sklearn.compose import Column Transformer
>
> num_cols = ['col_1','col_3']
> cat_cols = ['col_4']
> ord_cols = ['col_2','col_5']
> 
> col_transformer = ColumnTransformer([('num', num_pipeline, num_cols),
>                                      ('cat', cat_pipeline, cat_cols),
>                                      ('ord', ord_pipeline, ord_cols)]) # name, pipeline, columns
> ```


Definitons of terms used above:
* `SimpleImputer` - Imputes missing values for each feature in the training set, validation set, test set, and any new data fed to the model.
* `StandardScaler` - Used with numerical data. Scales all data uniformly to help features with large scales from dominating those with smaller scales.
* `OneHotEncoder` - Used with categorical data. Models can not handle categorical strings directly so this converts categories into a numerical format.
* `OrdinalEncoder` - Similar to OneHotEncoder but with ordinal data.
* `Data Leakage` - information from outside of the training set is used to create the model. This causes the model to learn something it should not know and can invalidate the results
* `Feature Engineering` - creating new features or transforming existing features to improve the performance of your model
