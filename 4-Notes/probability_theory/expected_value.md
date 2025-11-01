---
tags:
  - knowledge
  - probability-theory
---
我们如何统计一组数据的平均值，一个很平常的想法就是直接算这组数据的**算数平均值**，这对与均匀出现的数据可能是合理的，但是假如这些数据出现的概率**并不相等**。我们应该怎么更合理的估计它们的**平均值**

# General Definition
## Discrete Case
给定一个随机变量$X$，$X$的期望值是
$$
E[X] = \sum_{k} x_{k} P(X = x_{k})
$$
其实这种形式就是所有可能$X$取值的加权平均。

## Continuous Case
给定随机变量$X$以及其概率密度函数 `PDF` $f(x)$， $X$的期望是
$$
E[X] = \int ^{\infty}_{-\infty} x \cdot  f(x) dx
$$
**NOTE**：关于 `PDF`, `PMF`等等的相关概念请参考 [[concept_explanation_for_probability_theory]]

# Reference
[[concept_explanation_for_probability_theory]]