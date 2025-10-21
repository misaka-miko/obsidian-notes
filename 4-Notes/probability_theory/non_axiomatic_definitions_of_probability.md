---
tags:
  - knowledge
  - probability-theory
---
# Geometric Probability
Given a sample space $S$, the probability of event $A$ occurring is $P(A) = \frac{M(A)}{M(S)}$, where $M$ is the measure of geometric region

## example: 1-dimensional geometric probability
$X$ is a random real number between 1 and 2. What is the probability that $X$ is equal to 1.5?
**Solution**:
Dividing the $[1,2]$ into $2N+1$ equal parts
Using notation $A_{i}$ for $\left[ 1+\frac{i-1}{2N+1}, 1+\frac{i}{2N+1} \right]$
We have
$$
P(A_{i}) = \frac{1}{2N+1}
$$
Obviously, we have 
$$
1.5 \in \left[ 1+\frac{N}{2N+1}, 1+\frac{N+1}{2N+1} \right]
$$
so $0 \le P(X=1.5) \le P(A_{N+1})$
$\\lim_{ N \to \infty } P(A_{N+1}) = 0$
so $P(X=1.5) = 0$

## Insights from the example
- For Event $A$: $A = \emptyset, P(A) = 0$, $A$ is a **IMPOSSIBLE** Event
- For Event $B$: $P(B) = 0$, $B$ is a possible event