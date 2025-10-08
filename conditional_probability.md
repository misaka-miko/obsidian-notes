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
