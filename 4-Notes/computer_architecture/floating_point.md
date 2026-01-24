---
tags:
  - knowledge
category: computer architecture
topic: computer architecture
author: misaka
created:
  - 2026-01-22 11:52
---
👉 Go back to [[learning]]

> “95% of the folks out there are completely clueless about floating-point”
> - James Gosling, 1998-02-28

# Representation of Fraction
我们考虑一个简单的问题：给定一个$6$-bit的二进制数，并且它的小数点在左边第$2$位：
$$
x x .yyyy
$$
现在的问题是：他可以表达什么范围内的数字？

还记得我们之前讨论的基数吗，之前基数貌似都是非负的：$2^{0},2^{1},\dots$，如果我把这件事情向负数延申呢，我们找到了一个合理的方法表达**二进制小数**！
$$
10.1010_{2} = 1 \times 2^{1} + 1 \times 2^{-1} + 1 \times 2^{-3} = 2.625_{10}
$$

# Floating Point
但是这种**固定**小数点的做法是不是合理的呢，这貌似更像*fixed point*，如果我们还有一个输入可以告诉我们小数点应该在哪里呢？
举个例子，我们想要存储$0.1640625$，它的二进制表达如下：
$$
\dots 000000.00\mathbf{10101}0000\dots 
$$
我们是否需要存储其他的那些$0$？看起来**并不需要**，接下来，我需要有一位输入来告诉我小数点应该在我的*有效位*（energy）的左边两位：$-2$
- $10101$：energy，即有效位
- $-2$：浮点位置

## Scientfic Notation
回顾以下科学计数法：
$$
6.02 \times 10^{23}
$$
- $.$：decimal point
- $6.02$：尾数(*mantissa*)
- $10$：底数(*radix/base*)
- $23$：指数(*exponent*)
- Normalized form：no leading $0$s

那么**二进制**呢？这就是一件事!
$$
0.101_{2} = 1.01_{2} \times 2^{-1}
$$
## Floating Representation
- 标准格式：$+1.x x x\dots x_{2} \times 2^{yyy\dots y_{2}}$
- 给定一个$32$-bit的浮点数，我们怎么分配各个表示位：
	- $31$：符号位
	- $30 \to 23$：$8$-bit的exponent
	- $22 \to 0$：$23$-bit的significand

这非常**高效**，我们的浮点数现在可以储存$1.2\times 10^{-38} \to 3.4 \times 10^{38}$的范围了

但是，**代价**是什么呢？
- *overflow*：和整型一样，当我们试图储存的数字向$\infty$移动，我们会遭遇Overflow
- *underflow*：但是请记住我们的指数为在负方向上也是有限制的，你没有办法无限的减半某个浮点数，最后的结果类似于精度丢失

## IEEE 754
- 符号位：$1$表示负，$0$表示正
- 尾数(*significand*)
	- 为了能容纳更多位，默认前面有$1$
	- $1+23$ bits single, $1+52$ bits double
	- 一直有：$0 < \text{Significand} < 1$

**NOTE**: 事实上$0$没有leading $1$，我们这么做：专门为$0$保留指数为$0$的情况
- exponent: $0$
- significand: $0$
- sign bit: 你可以注意到有趣的地方了，我们有两个$0$