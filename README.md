# Data Science - blood & tears
My experience while working in Data Science, so I don't have to relearn or reinvent any thing.

1. Early Stopping, but when?

According to [this paper](http://page.mi.fu-berlin.de/prechelt/Biblio/stop_tricks1997.pdf), slower stopping criteria allow for small
improvements in generalization (here: about 4% on average), but cost much more training time (here: about factor 4 longer on average).

2. No Free Lunch theorem as I understand it

If we have absolutely no knowledge or insights about the problem we intend to solve, which algorithm we choose doesn't matter.

3. Bayes error rate

In statistical classification, [Bayes error rate](https://en.wikipedia.org/wiki/Bayes_error_rate) is the lowest possible error rate for any classifier of a random outcome (into, for example, one of two categories) and is analogous to the irreducible error.

4. [Common Dimension Reduction techniques](https://www.analyticsvidhya.com/blog/2018/08/dimensionality-reduction-techniques-python/)

![Dimension Reduction](image/dimension_reduction.png)

5. [Use backslash escapes in f-strings](https://realpython.com/python-f-strings/)

> As you saw earlier, it is possible for you to use backslash escapes in the string portion of an f-string. However, you can’t use backslashes to escape in the expression part of an f-string:

```
>>> f"{\"Hello World\"}"
  File "<stdin>", line 1
    f"{\"Hello World\"}"
                      ^
SyntaxError: f-string expression part cannot include a backslash
```

6. Compare notebooks for version control

Use [nbdime](https://nbdime.readthedocs.io/en/stable/#)

```
nbdiff notebook_1.ipynb notebook_2.ipynb
nbdiff-web notebook_1.ipynb notebook_2.ipynb
```

7. Jupyter notebook tools

* facets: Data visualization
* papermill: Parameter settings
* nbconvert: convert notebooks to other formats

8. [Close multiple Chrome windows with PowerShell](https://www.reddit.com/r/PowerShell/comments/5feoyx/one_liner_to_kill_chrome/)

```
Stop-Process -Name chrome
```

9. [Tukey test](https://www.statisticshowto.datasciencecentral.com/tukey-test-honest-significant-difference/)

> The Tukey Test (or Tukey procedure), also called Tukey’s Honest Significant Difference test, is a post-hoc test based on the studentized range distribution. An ANOVA test can tell you if your results are significant overall, but it won’t tell you exactly where those differences lie. After you have run an ANOVA and found significant results, then you can run Tukey’s HSD to find out which specific groups’s means (compared with each other) are different. The test compares all possible pairs of means.

10. SQL tips and tricks

* [Search for column name](https://stackoverflow.com/questions/26293085/find-all-table-names-with-column-name)

```
SELECT c.name AS ColName, t.name AS TableName
FROM sys.columns c
    JOIN sys.tables t ON c.object_id = t.object_id
WHERE c.name LIKE '%MyCol%';
```

* Declare a variable

```
DECLARE @my_var int = 10;
```

* Calculate a column using a calculated column

Not possible, recalculate.

* Read SQL script from file on Windows

Use `UTF-16` encoding, not `utf-8`

```
query = open(filepath, 'r',  encoding="UTF-16")
```

* [Parameterized query](https://stackoverflow.com/questions/43491381/pyodbc-the-sql-contains-0-parameter-markers-but-1-parameters-were-supplied-hy0)

* [create function must be the only statement in the batch](https://stackoverflow.com/questions/25002881/create-function-must-be-the-only-statement-in-the-batch) error

Add `GO` at the end of the function.

* Cannot save a sql file directly from a text file, must do that from MSSS (for now)

11. [Time series - ARMA model](https://www.datacamp.com/courses/arima-modeling-with-r)

You should always examine the residuals because the model assumes the errors are Gaussian white noise.
Test for white noise with `astsa` package in R

```
# Generate 100 observations from the AR(1) model
x <- arima.sim(model = list(order = c(1, 0, 0), ar = .9), n = 100) 

# Plot the generated data 
plot(x)

# Plot the sample P/ACF pair
plot(acf2(x))

# Fit an AR(1) to the data and examine the t-table
sarima(x, p = 1, d = 0, q = 0)
```

Bad residuals
* Pattern in the residuals
* ACF has large values
* Q-Q plot suggests normality
* Q-statistics - all points below line

12. [Various kinds of transformation for categorical variables](http://contrib.scikit-learn.org/categorical-encoding/index.html)

13. Jupyter Notebook tips and tricks

* [Template to import libraries in Jupyter Notebook](https://stackoverflow.com/questions/36194865/configure-a-first-cell-by-default-in-jupyter-notebooks)

Halfway solution: use the `%load` magic of IPython

* Autoreload submodule in Jupyter Notebook

```
%load_ext autoreload
%autoreload 2
```

* [Use joblib for caching output](https://hackernoon.com/10-tips-on-using-jupyter-notebook-abc0ba7028a4)

It's faster to cache repeated result with joblib

```
from sklearn.externals.joblib import Memory
memory = Memory(cachedir='/tmp', verbose=0)
@memory.cache
def computation(p1, p2):
    ...
```

* Interactive table

    * [Use DataTable](https://medium.com/@marekermk/guide-to-interactive-pandas-dataframe-representation-485acae02946)

    * Use [`qgrid`](https://github.com/quantopian/qgrid)

```python
import qgrid
# Adjust column width with grid_options
qgrid_widget = qgrid.show_grid(df, show_toolbar=True, grid_options={'forceFitColumns': False, 'defaultColumnWidth': 200})
qgrid_widget
```

        * Sometimes `qgrid.show_grid` does not work. One solution is to close and open notebooks once for `qgrid` to work. Not sure why yet. Can't reproduce on an isolated environment.

* [Display all columns with pandas](https://stackoverflow.com/questions/11707586/how-do-i-expand-the-output-display-to-see-more-columns)

Some related settings:

```python
pd.set_option('display.max_rows', 500)
pd.set_option('display.max_columns', 500)
pd.set_option('display.width', 1000)
```

* [Printing all the outputs of a cell](https://towardsdatascience.com/10-simple-hacks-to-speed-up-your-data-analysis-in-python-ec18c6396e6b)

```python
from IPython.core.interactiveshell import InteractiveShell
InteractiveShell.ast_node_interactivity = "all"

```

14. SVN on Windows tips and tricks

* [Add all unversioned files](https://stackoverflow.com/questions/1071857/how-do-i-svn-add-all-unversioned-files-to-svn) (This solution do not add ignored files)
```
svn --force add .
```

* Delete files

Cannot delete manually, must use `svn rm path/to/file`

* [Remove manually deleted files](https://stackoverflow.com/questions/9600382/svn-command-to-delete-all-locally-missing-files)

```ps
svn status | ? { $_ -match '^!\s+(.*)' } | % { svn rm $Matches[1] }
```

* After ignoring files, must commit for it to work.

15. Python tips and tricks

* Use [pytest `-s` flag](https://stackoverflow.com/questions/24617397/how-to-print-to-console-in-pytest) to print the statement to the console

* Use [MonkeyType](https://github.com/Instagram/MonkeyType) to automatically add type hint to legacy code.

* [Suppress LightGBM Warning](https://github.com/Microsoft/LightGBM/issues/1157)

For `sklearn` interface, set `verbose=-1` when defining the model (not in fit).

For `lgb.train` interface, you can set `verbose=-1` in param dict.

16. Financial data

*  We need to back-adjust all historical data for an instrument when there is a new split or dividend.

17. Cross Validation is used for [model comparison](https://stats.stackexchange.com/questions/52274/how-to-choose-a-predictive-model-after-k-fold-cross-validation), not model building

After we pick the suitable, we retrain with all the data and use that model for production.

18. Travis CI tips and tricks

* lint a travis.yml file

```console
travis lint [path to your .travis.yml]
```

19. Python toolbox

* Web Scrapping: BeautifulSoup
* Data Visualization: seaborn, matplotlib, facets, qgrid
* Feature Engineering: category_encoders
* Classical Machine Learning modelling: scikit-learn, LightGBM, CatBoost, XGBoost 
* Deep Learning modelling: Keras, Tensorflow, Pytorch
* Clustering: hdbscan
* Autoformat and linting: pylint, pycodestyle, pydocstyle
* Database: pyodbc
* Dimension Reduction: Factor Analysis, Principal Component Analysis, Independent Component Analysis, t-SNE (scikit-learn), UMAP
* Reporting: papermill, scrapbook

20. [Panel data](https://en.wikipedia.org/wiki/Panel_data)

In statistics and econometrics, panel data or longitudinal data are multi-dimensional data involving measurements over time.

21. R tips and tricks

* [Connect to an SQL database](https://stackoverflow.com/questions/49652986/import-dataframe-from-sql-server-into-r)

```r
library(RODBC)
dbhandle <- odbcDriverConnect('driver={SQL 
Server};server=mysqlhost;database=mydbname;trusted_connection=true')
res <- sqlQuery(dbhandle, 'select * from information_schema.tables')
```

22. [Comparison of Likelihood Ratio, Wald test and Rao's Score test](https://stats.stackexchange.com/questions/144603/why-do-my-p-values-differ-between-logistic-regression-output-chi-squared-test)

![Statistical tests' comparison](image/statistics_test_comparison.gif)

> * The Wald test assumes that the likelihood is normally distributed, and on that basis, uses the degree of curvature to estimate the standard error. Then, the parameter estimate divided by the SE yields a z-score. This holds under large N, but isn't quite true with smaller Ns. It is hard to say when your N is large enough for this property to hold, so this test can be slightly risky.
> * Likelihood ratio tests look at the ratio of the likelihoods (or difference in log likelihoods) at its maximum and at the null. This is often considered the best test.
> * The score test is based on the slope of the likelihood at the null value. This is typically less powerful, but there are times when the full likelihood cannot be computed and so this is a nice fallback option.

23. Trading algorithm testing

* White Reallity Check test
* Hansen Superior Predictive Ability test

24. Update Python syntax to a newer version

Use [`flynt`](https://github.com/ikamensh/flynt) or [`pyupgrade`](https://github.com/asottile/pyupgrade)

25. [Add new file types to Atom](https://flight-manual.atom.io/using-atom/sections/basic-customization/#customizing-language-recognition)

26. [Example of `tf.data.Dataset.from_generator`](https://stackoverflow.com/questions/52582275/tf-data-with-multiple-inputs-outputs-in-keras)

Note: Add `.repeat()` to loop infinitely.

```python
def _input_fn():
  sent1 = np.array([1, 2, 3, 4, 5, 6, 7, 8], dtype=np.int64)
  sent2 = np.array([20, 25, 35, 40, 600, 30, 20, 30], dtype=np.int64)
  sent1 = np.reshape(sent1, (8, 1, 1))
  sent2 = np.reshape(sent2, (8, 1, 1))

  labels = np.array([40, 30, 20, 10, 80, 70, 50, 60], dtype=np.int64)
  labels = np.reshape(labels, (8, 1))

  def generator():
    for s1, s2, l in zip(sent1, sent2, labels):
      yield {"input_1": s1, "input_2": s2}, l

  dataset = tf.data.Dataset.from_generator(generator, output_types=({"input_1": tf.int64, "input_2": tf.int64}, tf.int64))
  dataset = dataset.batch(2).repeat()
  return dataset

...

model.fit(_input_fn(), epochs=10, steps_per_epoch=4)
```

27. Download all files in a Jupyter Notebook server

In a cell, run `!tar chvfz notebook.tar.gz *`

28. [Save content of a web page to a file with the same name](https://stackoverflow.com/questions/13735051/how-to-capture-curl-output-to-a-file)

```
curl http://example.com/folder/big-file.iso -O
```

29. Choose ARMA parameters from ACF and PACF

![Choose ARMA parameters from ACF and PACF](image/ARMA_ACF_PACF.png)

30. Use the correct `alternative` option in Fisher Exact test

https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.fisher_exact.html

31. Scientific Python project template

https://github.com/scientific-python/cookie
