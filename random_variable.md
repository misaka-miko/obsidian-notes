# Definition
给定一个实验（样本空间$S$），一个随机变量(r.v.)是一个从样本空间$S$映射到实数$R$的函数

## Properties
1. $X$中的一个值可能对应多个结果
2. $X$中的不同值对应$S$中互斥的事件
3. $X$中的所有可能值形成$S$的一个划分

---
# Discrete Random Variable
## Definition
一个随机变量$X$是离散的，假如有有限的（或是无限的）一串数使得 $\sum_j P(X=a_j \text{ for some j}) = 1$. 如果说$X$是一个离散随机变量，那么有限集合或者可数无限集合中的$x$使得$P(X=x)>0$叫做$X$的支撑(*support of X*)

---
# Probability Mass Function(PMF)
## Definition
一个离散随机变量的PMF是
$$
p_X (x) = P(X=x)
$$
- $p_X>0$ 若$x$是$X$的一个支撑
- 否则 $p_X=0$

## Valid PMFs
> $X$是一个离散随机变量，有支撑$x_1, x_2,\ldots$是可数无限集合。那么$p_X$满足

1. $p_X >0$ if $x=x_j$ for some $j$, and $p_X(x) = 0$
2. $\sum^{\infty}_{j=1}p_X(x_j)= 1$