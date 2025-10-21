---
tags:
  - knowledge
  - probability-theory
---
### Summary
正态分布曲线，可以理解为**二项分布**的极限形式，但是值得注意的是，这并不是总是成立的，至少从模拟现实的角度来说不是（**当 $p$ 或者 $1-p$ 其中一个过于小的时候，正态分布曲线并不精确**）
在这种情况下参考 [[poisson_distribution]]
*For more about notation*: refer to [[notations]]

# Probability Mass Function
If we have r.v. $X \sim \mathcal{N}(np, npq)$, the `PMF` of $X$ is given as
$$
P(X = x) = \frac{1}{\sqrt{ 2 \pi  }\sigma } e^{-\frac{(x-\mu )^{2}}{2 \sigma^{2}}}
$$

# Ideas
## Meaning of $\sigma$
标准差在图像上的最大贡献就是决定了正态分布曲线的**离散程度**，参考下图

![different standard deviation](different_sd.png)

## Simulate Discrete