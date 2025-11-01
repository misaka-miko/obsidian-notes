---
tags:
  - knowledge
  - probability-theory
---
### Summary
如同我们在[[normal_distribution]]中所讲的那样，正态分布曲线并不能解决所有问题，至少不能很好的解决

![normal_diff](normal_diff.png)
由上图可以看出，如果说$np$过小，正态分布曲线的拟合效果并不好，于是我们就需要引入泊松分布 (*Poisson Distribution*)
# How to derive Poisson Distribution
在我们进行推导之前，首先需要指出的是*泊松分布*是为了**模拟**二项分布而推导出来的工具
回顾一下[[binomial_distribution]]，给定一个随机变量$X$，我们有
$$
P(X=k)=\binom{n}{k} p^{k}q^{n-k}
$$
我们将这个分布的期望，设为一个常量，$\lambda = np$，我们将上述公式进行展开
$$
P(X=k) = \frac{n!}{(n-k)!\cdot k!} p^{k} q^{n-k} = \frac{n(n-1)\ldots(n-k+1)}{k!} \cdot\frac{\lambda^{k}}{n^{k}} \cdot \left( 1-\frac{\lambda}{n} \right)^{n}\left( 1-\frac{\lambda}{n} \right)^{-k}
$$
$$
= \frac{\lambda^{k}}{k!} \cdot \frac{n(n-1)\dots(n-k+1)}{n^{k}}\cdot \left( 1-\frac{\lambda}{n} \right)^{n}\left( 1-\frac{\lambda}{n} \right)^{-k}
$$
到目前为止我们所做的只不过是等价变换，但是当$n \to \infty$时，有趣的事情出现了
$$
P(X=k) = \frac{\lambda^{k}}{k!} \cdot e^{-\lambda}
$$

## When should we use Poisson Distribution
稀有事件是我们所需要关心的，比如
- 地震
- 灯泡损坏率
- 自然灾害
- $\dots$
可是这些事件用正太分布的拟合效果并不好，**尽管在泊松分布最终也会趋于正态分布的前提下也是如此**
# Showcase
我们一直在强调正太分布在拟合这种$Bin(n,p)$中$p$过小的效果不好，但是这种不好的程度到底能有多大，参考下图 
![poisson normal and binomial](pois_norm_bin.png)

可以看到在$p$极小的情况下泊松分布的拟合效果是非常好的
# References
[[normal_distribution]]
[[binomial_distribution]]