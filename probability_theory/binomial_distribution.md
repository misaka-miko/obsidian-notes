二项式分布：假设我们执行$n$次**独立的**伯努利实验，成功的概率为$p$。令$X$为成功的次数。$X$的分布叫作二项式分布(**Binomial Distribution**)，我们记作
$$
X \sim Bin(n,p)
$$
其中$n>0, 0<p<1$

# Binomial PMF
若 $X \sim Bin(n,p)$，则有
$$
P(X=k) = \binom{n}{k} p^{k}(1-p)^{n-k}
$$
**Theorem**：若$X \sim Bin(n,p)$，令$q=1-p$（我们一般用$q$表示伯努利实验失败的概率）。有
$$
n-X \sim Bin(n,q)
$$
**Simple Proof**:
$$
P(X = n-k) = \binom{n}{n-k}p^{n-k}q^{n-n+k} = \binom{n}{k}q^{k}p^{n-k} = P(n-X =k)
$$
