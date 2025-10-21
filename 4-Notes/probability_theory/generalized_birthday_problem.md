---
tags:
  - knowledge
  - probability-theory
  - example
---
Theorem:
- Each of $k$ people has a random number drawn from $n$ values.
- If the probability that at least two people have the same numbers $50\%$, then $k \approx 1.18 \sqrt{ n }$

**Proof**:
Define Event $A$: At least 2 people have the same number
then Event $A^c$: No one shares the same number
$$
P(A^c) = \frac{n(n-1)\dots(n-k+1)}{n^k} = 1 \cdot \left( 1-\frac{1}{n} \right) \cdot \dots \cdot \left( 1-\frac{k-1}{n} \right)
$$
If $k \ll n$, $\left( 1-\frac{1}{n} \right) \approx e^{-\frac{1}{n}}$
$$
P(A^c) = 1 \times e^{- \frac{1}{n}} \times \dots \times e^{- \frac{k-1}{n}} \approx e^{- \frac{k^{2}}{2n}}
$$

# Application
- hash collision