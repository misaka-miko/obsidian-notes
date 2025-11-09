---
tags:
  - knowledge
  - date-structure
---
我们怎么样描述一个算法的快慢，难道只看*运行时间*就可以了吗，事实上并不是这样的，如果给定一个优秀的算法，在十年前的电脑上运行的速度，可能并没有一个较差的算法在现代电脑上运行的速度快。因此我们需要引入更加合理的方式来衡量一个算法的优劣，于是我们有了**复杂度**这个概念
# Big-O notation
渐进符号**忽略**一个函数中增长较慢的部分以及各项的常数，不同的 `Big-O` notation对应的含义：
- $\Theta$: 相等
- $O$: 小于
- $\Omega$: 大于
## Properties
- $f(n) = \Theta(g(n)) \Leftrightarrow f(n) = O(g(n)) \wedge f(n) = \Omega (g(n))$ 
- $f(n) + g(n) = O(\max(f(n), g(n)))$
- $f(n) \times g(n) = O(f(n)\times g(n))$
- $\forall a \neq 1,\log_{a}n=O(\log_{2}n)$
	- 由换底公式可知，任何对数函数无论底数为何，都有**相同**的增长率，因此大部分时候我们会省略底数，直接记作 $O(\log n)$

# Idea 
- 在研究**时间复杂度**的时候，我们通常使用 $O$ 符号，因为我们通常关心算法的上届，而不用关心用时的下界
- 最坏时间复杂度和$O$没有关系，因此用$\Theta$来标记最坏时间复杂度是可行的

# References
- [[learning]]
- [[master_theorem]]