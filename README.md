# Data Science - blood & tears
My experience while working in Data Science, so I don't have to relearn or reinvent any thing.

1. Early Stopping, but when?

According to [this paper](http://page.mi.fu-berlin.de/prechelt/Biblio/stop_tricks1997.pdf), slower stopping criteria allow for small
improvements in generalization (here: about 4% on average), but cost much more training time (here: about factor 4 longer on average).

2. No Free Lunch theorem as I understand it

If we have absolutely no knowledge or insights about the problem we intend to solve, which algorithm we choose doesn't matter.

3. Bayes error rate

In statistical classification, [Bayes error rate](https://en.wikipedia.org/wiki/Bayes_error_rate) is the lowest possible error rate for any classifier of a random outcome (into, for example, one of two categories) and is analogous to the irreducible error.

4. Common Dimension Reduction techniques

(Reference: https://www.analyticsvidhya.com/blog/2018/08/dimensionality-reduction-techniques-python/)

![Dimension Reduction](image/dimension_reduction.png)

5. Use backslash escapes in f-strings

(Reference: https://realpython.com/python-f-strings/)

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

8. Close multiple Chrome windows with PowerShell

(Source: https://www.reddit.com/r/PowerShell/comments/5feoyx/one_liner_to_kill_chrome/)

```
Stop-Process -Name chrome
```

9. svn related problem

(Source: https://stackoverflow.com/questions/1598968/add-all-unversioned-files-to-svn)

* Add all unversioned files (Warning: This solution also adds all ignore files)
```
svn --force add .
```

10. Tukey test

(Source: https://www.statisticshowto.datasciencecentral.com/tukey-test-honest-significant-difference/)

> The Tukey Test (or Tukey procedure), also called Tukey’s Honest Significant Difference test, is a post-hoc test based on the studentized range distribution. An ANOVA test can tell you if your results are significant overall, but it won’t tell you exactly where those differences lie. After you have run an ANOVA and found significant results, then you can run Tukey’s HSD to find out which specific groups’s means (compared with each other) are different. The test compares all possible pairs of means.

11. Search for column name in SQL

(Source: https://stackoverflow.com/questions/26293085/find-all-table-names-with-column-name)

```
SELECT c.name AS ColName, t.name AS TableName
FROM sys.columns c
    JOIN sys.tables t ON c.object_id = t.object_id
WHERE c.name LIKE '%MyCol%';
```

12. Time series - ARMA model

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
