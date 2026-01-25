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

### How to deal with Exponent 
我们之前提到了指数$0$专门为了表示$0$这个数，但是这合理吗，我可能更希望指数的最小位表达了一个负数，这样我就可以有$2^{-x x x}$，可以表达某个小数，这不是更直观一些吗
- 更大的整数指数就是更大的数字
- 较小的表达分数
- 这就是为什么*2's complement*不能满足我们的要求：负数的表达看起来更大
- **更聪明的做法**：直接将我们实际的表达范围(比如说*0 - 255*)，减去一个*bias*，向下平移

我们有了这样的公式
$$
(-1)^{s} \times (1+\text{Significand}) \times 2^{\text{Exponent} - 127}
$$
其中$\text{bias} = 2^{8-1}-1 = 127$

# Special Numbers 
事实上，在我们之前定义浮点数中的$0$的时候，我们就可以发现似乎我们对于浮点数的存储方式的一些**边界情况**更加复杂

## Infinity
无穷是非常好用的，比如我们想要做一些迭代的*max*操作，那么我们选的初始值是什么？
很显然$-\infty$非常合理

IEEE 754如何表达 $\pm \infty$：
- 保留最大的指数：$2^{8} -1$
- significand都是$0$

为什么尾数是$0$：
我们认为$\infty$应该是最大的浮点数加1：
$$
1.111\dots 1_{2} \times 2^{11111110_{2}}+1 = 1.000\dots 0 \times 2^{111\dots 1}
$$

## Zero 
怎么表达$0$：
- 指数都是$0$
- 尾数都是$0$
- 符号位都是有效的

## Representation of Not a Number 
假如我们要计算 `sqrt(-4.0)` 或者 $\frac{0}{0}$？
- 假如说$\infty$不是一个错误(*overflow*)，那么这些也不应该是
- 称为**N**ot **a** **N**umber *NaN*
- 指数$255$，尾数非零

为什么NaN有用？
- 帮助调试
- contaminate: `op(NaN, X) = NaN`
- 可以用不同的尾数表达不同的NaN

## Representation of Denorms
事实上，我们能表达的最小的FP和零之间还是有间隙
- 最小的可表达的positive FP
	- $a = 1.0\dots_{2} \times 2^{-126}=2^{-126}$
- 第二小的可表达的positive FP
	- $b = 1.000\dots 1_{2} \times 2^{-126}=2^{-126} + 2^{-149}$
- $a-0 = 2^{-126}$
- $b-a = 2^{-149}$

我们怎么解决这个巨大的gap？**Denormalization**：
- no implicit leading $1$, implicit exponent $-126$
- 最小的可表达的正数：
	- $a = 2^{-149}$
- 第二小的可表达的正数：
	- $b=2^{-148}$
## Table of special numbers
| exponent | significand | object        |
| -------- | ----------- | ------------- |
| 0        | 0           | 0             |
| 0        | nonzero     | Denorms       |
| 1-254    | anything    | +/- fl. pt. # |
| 255      | 0           | $\pm \infty$  |
| 255      | nonzero     | NaN           |

# Floating Point Issues
浮点运算不满足**结合律**：
- 如果我们用一个非常大的浮点数，比如说$1.5\times 10^{38}$，去加一个非常小的浮点数，比如$1.0$，我们会有精度损失
- 对于大浮点数，它的步进远大于$1.0$，其实就是**没有足够的精度**去储存相对微小的变化

## Precision and Accuracy
- *Precision* is a count of the number bits in used to represent a number
- *Accuracy* is the difference between the actual value of a number and its computer representation
- 高精度**允许**高准确度，但是**不保证**高准确度

## IEEE Rounding Modes
- 向$+\infty$舍入：
	- Always Up
- 向$-\infty$舍入：
	- Always Down
- 截断(*truncate*)
	- 直接丢掉最后一位 (round towards $0$)
- 无偏(*unbiased*)，在中间的话就舍入为偶数
	- $2.4 \to 2$, $2.6 \to 3$, $2.5 \to 2$, $3.5 \to 4$