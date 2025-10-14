---
tags:
  - knowledge
  - probability-theory
---
**什么是伯努利分布**:一个随机变量$X$是伯努利分布若
$$
P(X=1) = p, P(X=0)=1-p
$$
其中$0<p<1$，记作$X \sim Bern(p)$

# Indicator Random Variable
> 事件$A$的 *indicator random variable*是一个随机变量满足 $I(A)=1$若$A$发生，$A$的 indicator r.v. 记作 $I_A$或 $I(A)$。注意 $I_A \sim Bern(p)$其中 $p=P(A)$

# Bernoulli Trial
**Definition**：一个实验的结果要么是*成功*要么是*失败*，则我们称这个实验是 **Bernoulli trial**

如果我们执行$n$次独立的Bernoulli trial，我们则将其称为[[binomial_distribution]]