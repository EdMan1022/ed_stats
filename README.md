# ed_stats
## Implementation of ANOVA and MANOVA methods, using pandas DataFrames

The package includes several functions, which take pandas dataframes, the string name of the independent variable column, a list of the columns that represent the dependent variables, and any additional function specific arguments. They return the results of several different types of variance analysis.

---


__anova(input\_data, group\_column, columns=None)__

Calculates a simple [one way ANOVA](https://en.wikipedia.org/wiki/One-way_analysis_of_variance) for each dependent variable given in columns. If no argument is passed for columns, returns a result for every column in input\_data that isn't group\_column. Returns a result dataframe containing the mean variance between independent variable groups, the mean variance within these groups, the calculated f statistic, and the p value associated with this f statistic and the data set's degrees of freedom.


---

__factorial\_anova(input\_data, group\_column, columns=None, n\_factors=3)__

First uses [Scikit-Learn's Principle Component Analysis](http://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html#sklearn.decomposition.PCA) to reduce the dependent variables specified in columns to the smaller number of factors defined by n\_factors. Then, performs one way ANOVAs for each of these new factors. Returns the same result dataframe as anova() does.


---

__manova(input\_data, group\_column, columns=None)__

Calculates a [MANOVA](https://en.wikipedia.org/wiki/Multivariate_analysis_of_variance) for the input data, with independent variable given by group\_column and dependent variables given in columns.  Returns a result dataframe containing the values of several tests; [Wilks Lambda](http://www.statisticshowto.com/wilks-lambda/)(rejects null hypothesis when value is low), Hotelling [Lawley Trace](http://www.real-statistics.com/multivariate-statistics/multivariate-analysis-of-variance-manova/manova-basic-concepts/)(rejects null hypothesis when value is large), and [Phillai Bartlett Trace](http://www.real-statistics.com/multivariate-statistics/multivariate-analysis-of-variance-manova/manova-basic-concepts/)(rejects null hypothesis when value is large).
