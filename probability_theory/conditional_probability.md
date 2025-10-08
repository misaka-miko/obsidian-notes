---
tags:
  - knowledge
  - probability-theory
---
条件概率(*conditional probability*)：描述给定条件下某个时间的发生概率
**IDEA**：本质是对样本空间的替换
$$
P(A) = P(A|S) = \frac{P(A \cap S)}{P(S)} = \frac{P(A)}{1}
$$
we have formula:
$$
P(A|B) = \frac{P(A \cap B)}{P(B)}
$$
# Properties
conditional probability still follow **similar** properties with normal probability
- $0 \leq P(A|E) \leq  1$ with $P(S|E) = 1$ and $P(\emptyset | E) = 0$
- For disjoint events $A_{1}, A_{2} \dots$, $P(\cup ^{\infty}_{j=1}A_{j}) = \sum_{j=1}^{\infty}P(A_{j})$
- inclusion-exclusion: $P(A \cup B | E) = P(A |E)+P(B| E) - P(A \cap B|E)$

## Chain rule
通过条件概率的公式，我们不止可以计算条件概率，我们也可以计算同时发生的概率
$$
P(A \cap B) = P(B)P(A|B) = P(A) \times P(B|A)
$$
如果我们有$n$个事件呢
$$
P(A_{1},A_{2}\dots A_{n}) = P(A_{1})P(A_{2}|A_{1})\dots P(A_{n}|A_{1},A_{2},\dots ,A_{n-1})
$$
公式含义：$n$个事件同时发生本质上是第一件事情发生的概率 $\times$ 第二件事在第一件事发生下的条件概率 $\times \dots \times$ 第$n$件事在前$n-1$件事发生下的条件概率

## The Law Of Total Probability (全概率公式)
给定 $A_{1}, A_{2},\dots,A_{n}$是$S$的一个划分
$$
P(B) = \sum_{i=1}^{n}P(B|A_{i})P(A_{i})
$$

# Associated Contents
- [[independence]]