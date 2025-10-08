---
tags:
  - knowledge
  - probability-theory
---
所谓*独立性*，就是一个事件的发生与否是否影响另一个事件的发生
独立性检验：
$$
P(A \cap B) = P(A) P(B)
$$
这并不符合我们的直观，独立性实际上可以粗暴的理解为
> 有没有都一样

$$
P(A) = P(A|B), P(B) = P(B|A)
$$
If you are not familiar with conditional probability, refer to [[conditional_probability]].

# Independence vs. Disjoint 
区分一下这两个容易混淆的概念：**独立性**与**互斥性**
**Example**：丢一个十面骰子
$A: \text{outcome is less than 7}$
$B: \text{outcome is an even number}$
$$
P(A) = \frac{3}{5}, P(B) = \frac{1}{2}, P(A \cap B) = \frac{3}{10}
$$
$$
P(A \cap B) = P(A) P(B)
$$
满足独立性，但是显然 $A$, $B$ 并非互斥

类似的互斥并不意味着独立

# Properties
## Independence of Complementary Set
If $A$ and $B$ are independent, then $A^{c}$ and $B$ are independent, $A$ and $B^{c}$ are independent, 
$A^{c}$ and $B^{c}$ are independent

## Independence of Three events
Events $A$, $B$, $C$ are independent if
1. $P(A \cap B) = P(A)P(B)$
2. $P(C \cap B) = P(C)P(B)$
3. $P(A \cap C) = P(A)P(C)$
4. $P(A \cap B\cap C) = P(A)P(B)P(C)$

## Conditional Independence
Like what I said in [[conditional_probability]], conditional probability is **somewhat** nothing special.

> Events $A$ and $B$ are said to be conditionally independent given $E$ if:

$$
P(A \cap B | E) = P(A|E) P(B|E)
$$
**WARNING**: conditional independent $\neq$ independent
**WARNING**: given $E$ conditional independent $\neq$  given $E^{c}$ conditional independent

## Simplify Computing
If events $A_{1}, A_{2},\dots,A_{n}$ are independent, then
$$
P(A_{1}\cap A_{2} \cap \dots \cap A_{n}) = \prod_{i=1}^{n}P(A_{i})
$$
$$
P(A_{1} \cup A_{2}\cup\dots \cup A_{n}) = 1- \prod_{i=1}^{n}(1-P(A_{i}))
$$
