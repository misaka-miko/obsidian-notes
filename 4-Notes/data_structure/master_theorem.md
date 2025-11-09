---
tags:
  - knowledge
  - date-structure
---
**Master Theorem**给我们提供了计算递归算法时间复杂度的方法
# Content of the Theorem
## Formula
如果给定以下递推表达式
$$
T(n) = aT\left( \frac{n}{b} \right)+f(n)
$$
有以下公式
$$
T(n) = 
\begin{cases}
\Theta(n^{\log_{b}a}) & f(n)=O(n^{\log_{b}(a) - \epsilon }), \epsilon>0 \\
\Theta(f(n)) & f(n)=\Omega(n^{\log_{b}(a) + \epsilon }), \epsilon \ge 0 \\
\Theta(n^{\log_{b}a}\log ^{k+1}n) & f(n)=\Theta(n^{\log_{b}a}\log ^{k}n),k \ge 0
\end{cases}
$$

# Idea 
事实上我们可以有一个简化版本的主定理
若给定$T(n)=aT\left( \frac{n}{b} \right)+\Theta(n^{d})$
$$
T(n)=
\begin{cases}
\Theta(n^{\log_{b}a}) & d<\log_{b}a \\
\Theta(n^{d}\log n) & d=\log _{b}a \\
\Theta(n^{d}) & d>\log_{b}a
\end{cases}
$$

# References
- [[learning]]
- [[complexity]]