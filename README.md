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
