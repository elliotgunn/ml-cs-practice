the guide to preprocessing:

1. Column transforming
- convert all values to numerical
    - one-hot encoding or dummy coding
    - to_datetime
    - [sklearn.compose.ColumnTransformer](https://scikit-learn.org/stable/modules/generated/sklearn.compose.ColumnTransformer.html) applies different preprocessing per columns
    - O'Reilly guide to transformations [[link]](https://www.oreilly.com/library/view/introduction-to-machine/9781449369880/ch04.html)

2. Encoding dirty categories (e.g. overlapping categories, high cardinality, rare categories, new categories in test set)
    - [similarity encoding](https://github.com/dirty-cat/dirty_cat/)

3. Learning with missing values
    - Categorical variables: create "missing" category
    - Numerical variables:
        - have to consider whether the missing data occurs randomly or not
        - [mean imputation](https://scikit-learn.org/stable/modules/generated/sklearn.impute.SimpleImputer.html), this distorts the distribution but for a powerful learner, imputing both train and test with the mean of train is consistent (converges to the best possible prediction)
        - [conditional imputation](https://scikit-learn.org/stable/modules/generated/sklearn.impute.IterativeImputer.html): modeling one feature as a function of others
        - use HistGradientBoosting

Sources:
[Machine learning on non curated data](https://www.slideshare.net/GaelVaroquaux/machine-learning-on-non-curated-data-154905090)

[HistGradientBoosting](https://easychair.org/publications/open/pCtK)
