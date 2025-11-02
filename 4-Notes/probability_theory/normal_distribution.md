---
tags:
  - knowledge
  - probability-theory
---
### Summary
正态分布曲线，可以理解为**二项分布**的极限形式，但是值得注意的是，这并不是总是成立的，至少从模拟现实的角度来说不是（**当 $p$ 或者 $1-p$ 其中一个过于小的时候，正态分布曲线并不精确**）
在这种情况下参考 [[poisson_distribution]]
*For more about notation*: refer to [[notations]]

# Probability Density Function
If we have r.v. $X \sim \mathcal{N}(np, npq)$, the `PDF` of $X$ is given as
$$
f(x)= \frac{1}{\sqrt{ 2 \pi  }\sigma } e^{-\frac{(x-\mu )^{2}}{2 \sigma^{2}}}
$$

# Ideas
## Meaning of $\sigma$
标准差在图像上的最大贡献就是决定了正态分布曲线的**离散程度**，参考下图

![different standard deviation](different_sd.png)

## Simulate Discrete
很多时候，我们如果要求$X$等于某个特定的$k$，这是我们所擅长的，但是试想以下情况$\ldots$
给定随机变量$X \sim Bin(n, p)$，其中$n=100$, $p=0.5$，我们需要求 $P(70 \le X \le 89)$，而这件事如果要用二项分布的概率公式来加和计算的计算量显然是**非常非常大的！！**
但是聪明你知道，我们在这种$p$的大小正正好好的场景下，正态分布曲线和二项分布曲线非常接近，我们或许使用正态分布来干一些事情$\dots$

### `CDF` of normal distribution
给定概率累计函数 $F(x)$，其表达的含义参考[[concept_explanation_for_probability_theory#What is `CDF`]]，我们所要求的$P(70 \le X \le 89)$实际上就是 $F(89)-F(70)$。虽然正态分布的`CDF`对于人类来说也不是那么友好，但是对于计算机来说，这种近似的优化是**非常大**的，精度损失也非常小，大部分情况下忽略不计。

# Reference
- [[binomial_distribution]]
- [[poisson_distribution]]
- [[concept_explanation_for_probability_theory]]