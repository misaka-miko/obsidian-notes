---
tags:
  - knowledge
category: computer architecture
topic: computer architecture
author: misaka
created:
  - 2026-01-25 15:20
---
👉 Go back to [[learning]]

# RISC-V Introduction

## Assembly Language 
- CPU的工作：执行大量指令
- 指令就是CPU可以执行的原始的操作
- 不同的CPU的**指令集**不同，特定CPU实现的指令集叫*Instruction Set Architecture* (ISA)
	- ARM(手机)
	- Intel x86
	- IBM Power
	- $\dots$

## RISC-V Architecture
为什么选择RISC-V？
- 简单，优雅
- 开源，生态良好
- 有$32$-bit, $64$-bit, $128$-bit variants

## RISC-V elements

### 寄存器
- 不同于high level language，汇编中并没有*变量*
	- 为了让硬件更简单
- 汇编的操作对象是寄存器(*registers*)
	- 有限个被构建在硬件中的特殊位置
	- 任何操作只能作用在寄存器上
- 这有什么好处呢？
	- 速度极快(faster than $0.25$ns)a
- 寄存器既然这么快速，那么为什么我们不大量使用寄存器来加快cpu运行速度呢？
	- 寄存器直接构建在硬件内，我们只能有**有限数量**的寄存器
	- 汇编中需要写出高效利用寄存器的代码
- RISC-V中有$32$个寄存器
- 在$32$位的寄存器中，每个寄存器都是$32$ bit宽的，被称为字(*word*)
- 寄存器被从$0$到$31$编号
	- 可以通过 `x0 - x31`访问
	- `x0`是特殊的，总是保存$0$
	- 实际上只有$31$个寄存器可以保存变量值
- 每个寄存器都可以通过**数字**或者**名字**访问

所以*寄存器*和*变量*有什么区别
- 变量：在大部分HHL中，变量的声明必须指定类型
	- 支持的操作
	- 分配的内存
- 在汇编中，寄存器没有类型

## Assembly Instructions
- 在汇编中，一个statement被称为指令(*instruction*)，执行一个命令列表中的一条命令
- 汇编每行只能有**至多**一条指令
- 指令包含一些基本操作(=, +, -, \*, /)

## RISC-V Add/Sub Instructions
指令的语法是什么：`one two, three, four`
```risvc
add x1, x2, x3
```
- `one`: 操作名
- `two`: 得到结果的操作对象(*destination*)
- `three`: 操作的第一个操作对象(*source 1*)
- `four`: 操作的第二个操作对象(*source 2*)

**汇编加法**：
`add x1, x2, x3` $\Leftrightarrow$ `x1 = x2 + x3`

**汇编减法**：
`sub x1, x2, x3` $\Leftrightarrow$ `x1 = x2 - x3`

## RISC-V Immediates
什么是立即数(*immediate*)：就是**numerical constant**
加一个立即数：
```riscv
addi x3, x4, 10
```