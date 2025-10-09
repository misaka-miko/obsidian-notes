---
tags:
  - knowledge
  - probability-theory
---
> Bayes's rule deals with how we update our belief

# General definition
Given event $A$ and $B$, we have
$$
P(A|B) = \frac{P(A)P(B|A)}{P(B)}
$$
**notation explanation**:
- $P(A|B)$: posterior probability
- $P(A)$: prior probability
- $P(B|A)$: likelihood

# `LOTP` Form 
事实上$P(B)$经常不能直接获得，我们往往需要寻求全概率公式
$$
P(A|B) = \frac{P(A)P(B|A)}{P(A)P(B|A) + P(A^{c})P(B|A^{c}))}
$$
# Story Explanation
事实上直接照着公式去理解 *bayes' rule*是困难的，这里给出一个故事来解释这个公式
> 我们描述张三的性格特征是温和内向，彬彬有礼的，现在我们需要做出一个判断，张三更有可能是一个大学生，还是更有可能是一个农民

可能我们会下意识的说张三更有可能是一个大学生，但是这是**非理性**的。因为我们并没有考虑大学生和农民之间的人数差距

我们不妨定义一个事件$H$($H$ For *Hypothesis*)：张三是一个大学生。那么$P(E)$是什么呢，实际上就是中国大学生和农民的人数比，为了分析方便，我们不妨认为这个数值是$1:10$
$$
P(H) = \frac{1}{1+10} \approx 9\%
$$
由于概率可能没有这么直观，我们不妨直接考虑实际的样本空间，比如说我们有$10$个学生和$100$个农民
现在我们获得了一个事件$E$($E$ For *Evidence*)：张三性格温和内向，彬彬有礼。