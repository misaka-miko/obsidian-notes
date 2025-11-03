---
tags:
  - knowledge
  - probability-theory
---
Given a sample space $S$, the class of subset of $S$ satisfy the following axioms
- $S$ is an event.
- For every event $A$, the complement $A^{c}$ is an event.
- For every sequence of events $A_{1}, A_{2}\dots$, the union $\bigcup_{j=1}^{\infty} A_{j}$ is an event.

# General definition of Probability
A probability space consists of a sample space $S$ and a probability *function* $P$  which maps an event $A$ to a **real number** which is in $[0,1]$ 
- $P(\emptyset) = 0$ , $P(S) = 1$
- If $A_{1}, A_{2}, \dots$ are **disjoint** events(互斥事件), then
$$
P\left( \bigcup_{j=1}^{\infty}A_{j} \right) = \sum^{\infty}_{j=1} P(A_{j})
$$

# Properties of Probability
For any event $A$ and $B$
1. $P(A) = 1- P(A^{c})$
2. If $A \subseteq B$, then $P(A) \leq P(B)$
3. $P(A \cup B) = P(A) + P(B) - P(A \cap B)$

**Theorem**: For any events $A_{1}, A_{2} ,\dots, A_{n}$, we have
$$
P(A_{1}\cap \dots \cap A_{n}) \geq \sum_{j=1}^{n} P(A_{j}) -(n-1)
$$
**Proof**: 
$$
P(A_{1}\cap \dots \cap A_{n}) \leq \sum_{j=1}^{n} P(A_{j}) -(n-1) \Leftrightarrow 1- P(A_{1} \cap \dots \cap A_{n}) \geq n - \sum_{j=1}^{n}P(A_{j})
$$
$$
\Leftrightarrow P(\overline{A_{1}\cap\dots \cap A_{n}}) \leq \sum_{j=1}^{n} (1- P(A_{j})) = \sum_{j=1}^{n}P(\overline{A_{j}})
$$
**Theorem**: For any events $A_{1}, A_{2}, \dots$, we have
$$
P\left( \bigcup^{\infty}_{j=1} A_{j} \right) \leq \sum_{j=1}^{\infty} P(A_{j})
$$

## Inclusive-exclusive formula
For any events $A_{1}, A_{2}, \dots, A_{n}$:
$$
P\left( \bigcup_{i=1}^{n} A_{i} \right) = \sum_{i}P(A_{i}) - \sum_{i<j} P(A_{i} \cap A_{j}) + \sum_{i<j<k}P(A_{i} \cap A_{j} \cap A_{k}) + \dots + (-1)^{i+1}P(A_{1} \cap \dots \cap A_{n})
$$

# References
- [[learning]]