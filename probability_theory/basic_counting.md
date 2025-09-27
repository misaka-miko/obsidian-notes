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