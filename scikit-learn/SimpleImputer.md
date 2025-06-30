# SimpleImputer
`python` `scikit-learn`

## What Does SimpleImputer Do?
`SimpleImputer` is used to replace missing values in your data. This is an essential class to use since most machine
learning models do not work effectively or at all when the data has missing values. </br>
</br>
The different strategies you can use are:
* `mean` - missing values replaced with the mean of that column
* `median` - missing values replaced with the median of that column
* `most_frequent` - missing values replaced with the mode of that column
* `constant` - missing values replaced with specified value for that column
  * must pair with `fill_value` to specify what constant

Example:
> ```python
> from sklearn.impute import SimpleImputer
>
> imputer = SimpleImputer() # default is mean
>
> imputer.fit_transform(df)
> ```

## Common Practices
Most of the time, your data will contain different data types. Some columns you may want to impute the null values with the 
median and some you may want to use the most frequent value. This can be achieved by specifying which strategy your SimpleImputer
is using within your specific pipeline to then be applied within a column transformer OR just straight in a column transformer.</br>
</br>
Examples of both ways:
> ```python
> from sklearn.impute import SimpleImputer
> from sklearn.pipeline import make_pipeline
> from sklearn.compose import make_column_transformer
> from sklearn.compose import ColumnTransformer
> from sklearn.preprocessing import OneHotEncoder
> from sklearn.preprocessing import StandardScaler
>
> ## example 1
> mean_imputer = SimpleImputer(strategy='mean')
> mode_imputer = SimpleImputer(strategy='most_frequent')
> preprocessing = make_column_transformer((mean_imputer, ['column_name_1']), (mode_imputer, ['column_name_2']), remainder='drop')
> df_prepared = preprocessing.fit_transform(df)
>
> ## example 2
> num_cols = ['col_1','col_2']
> cat_cols = ['col_3','col_4']
> num_pipeline = make_pipeline(SimpleImputer(strategy='mean'), StandardScaler())
> cat_pipeline = make_pipeline(SimpleImputer(strategy='most_frequent'), OneHotEncoder())
> preprocessing = ColumnTransformer([('num', num_pipeline, num_cols),('cat', cat_pipeline, cat_cols)])
> df_prepared = preprocessing.fit_transform(df)
> ```
