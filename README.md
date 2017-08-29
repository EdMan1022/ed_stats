# ed_stats
## Implementation of ANOVA and MANOVA methods, using pandas DataFrames

The package includes several functions, which take pandas dataframes, the string name of the independent variable column, a list of the columns that represent the dependent variables, and any additional function specific arguments. They return the results of several different types of variance analysis.

---

anova(input_data, group_column, columns=None)

Calculates a simple [one way ANOVA](https://en.wikipedia.org/wiki/One-way_analysis_of_variance) for each dependent variable given in columns. If no argument is passed for columns, returns a result for every column in input_data that isn't group_column. Returns a result dataframe containing the mean variance between independent variable groups, the mean variance within these groups, the calculated f statistic, and the p value associated with this f statistic and the data set's degrees of freedom.
---

factorial_anova(input_data, group_column, columns=None, n_factors=3)

First uses [Scikit-Learn's Principle Component Analysis](http://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html#sklearn.decomposition.PCA) to reduce the dependent variables specified in columns to the smaller number of factors defined by n_factors. Then, performs one way ANOVAs for each of these new factors.
