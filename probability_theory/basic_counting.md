# Overall table

|                     | order matters       | order not matter     |
| ------------------- | ------------------- | -------------------- |
| with replacement    | $n^{k}$             | $\binom{n+k-1}{k-1}$ |
| without replacement | $\frac{n!}{(n-k)!}$ | $\binom{n}{k}$       |

---
# Ordered Sampling with Replacement
> Choosing $k$ objects from a set with $n$ objects, one at a time with replacement
> Then there are $n^k$ possible outcomes

---
# Ordered Sampling without Replacement
> Choosing $k$ objects from a set with $n$ objects, one at a time without replacement. 
> Then there are $n(n-1) \dots (n-k+1)$ possible outcomes for $k \le n$ (and $0$ for $k > n$). When $k = n$, there are $n!$ possible outcomes, each outcome is called a "permutation" of such $n$ objects.

the formula can also be written as
$$
\frac{n!}{(n-k)!}
$$
## example: generalized birthday problem
[[generalized_birthday_problem]]

---
# Unordered Sampling without Replacement
- also called **Combination**
- k-combination: choose a k-element subset of a set with $n$ elements.

> For $k \le n$, we have

$$
\binom{n}{k} = \frac{n!}{k!(n-k)!}
$$
For more about binomial theorem, refer to [[binomial_theorem]]
For more information about **story proof**, refer to [[story_proof]]

---
# Unordered Sampling with Replacement
**Equivalent Problem**
$$
x_{1}+x_{2}+\dots+x_{n} = k, \forall n > 0,k \ge 0, x_{i} \geq 0
$$
- $x_{i}$ : 第i个物体被选中的次数
- 总共被选中的次数是$k$
The number of the **non-negative** solution vectors is $\binom{n+k-1}{n-1}$