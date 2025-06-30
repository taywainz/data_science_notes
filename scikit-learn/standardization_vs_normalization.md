# Feature Scaling
`python` `scikit-learn`

## What is Feature Scaling?
Feature scaling is a preprocessing technique used to improve your model's performance by converting _numerical_ values 
into the same scale. This is a crucial technique since many models do not perform well when input features have different scales
or units (ex: income in thousands vs age in years).</br>
</br>
The two most common methods are **standardization** and **normalization**.

> [!IMPORTANT]
> Feature scaling is typically applied within your numeric pipeline, but the examples below will show basic ways on how the class is instantiated.

## Standardization
Also referred to as `Z-score scaling`, standardization transforms data to have a standard deviation of 1 and a mean of 0.
This means after standardizing your data, values that are negative are considered 'below average'.</br>
</br> 
Algorithms that benfit from standardization:
* SVMs (Support Vector Machine)
* K-Means
* Dimensionality Reduction like PCA (Principal Component Analysis)

The example below shows how to apply standardization using sklearn's `StandardScaler` 

>```python
> from sklearn.preprocessing import StandardScaler
>
> scaler = StandardScaler()
>
> num_cols_scaled = scaler.fit_transform(num_cols)

## Normalization
Min-max normalization transforms your data to a fixed range (often 0 to 1). This means after normalizing your data, the largest
value is now depicted as 1, and the lowest value is depicted as 0.</br>
</br>
Algorithms that benefit from normalization:
* Unknown or Non-Gaussian Distribution (skewed data, multiple peaks, etc)
* Distance-Based like KNN (K-Nearest Neighbors)

The example below shows how to apply normalization using sklearn's `MinMaxScaler` 
> ```python
> from sklearn.preprocessing import MinMaxScaler
>
> scaler = MinMaxScaler() # can specify feature_range
>
> num_cols_scaled = scaler.fit_transform(num_cols)
