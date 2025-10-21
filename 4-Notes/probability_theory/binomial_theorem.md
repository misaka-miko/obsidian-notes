---
tags:
  - knowledge
  - probability-theory
---
# Binomial Theorem
$$
(x+y)^{n} = \sum ^{n}_{k=0} \binom{n}{k} x^{k}y^{n-k}
$$
# Multinomial Theorem
## Simple example
dividing 10 people into **three** groups, with number 5, 3 and 2. We have
$$
\binom{10}{5} \binom{5}{3} \binom{2}{2} = \frac{10!}{5! \times 5!} \times \frac{5!}{3! \times 2!} \times \frac{2!}{2!\times 0!} = \frac{10!}{5! \times 3! \times 2!} = \binom{10}{5,3,2}
$$

## Theorem
$$
(x_{1}+x_{2}+\dots+x_{r})^{n} = \sum_{n_{1},n_{2},\dots ,n_{r} \ge 0}\binom{n}{n_{1},n_{2}\dots n_{r}}x_{1}^{n_{1}}x_{2}^{n_{2}}\dots x_{r}^{n_{r}}
$$
where $n_{1}+n_{2}+\dots+n_{r} = n$
