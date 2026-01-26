---
tags:
  - knowledge
category: computer architecture
topic: computer architecture
author: misaka
created:
  - 2026-01-25 22:12
---
👉 Go back to [[learning]]

# Storing Data in Memory
## Review: RV32 So Far
```asm
# addition
add rd, rs1, rs2

# subtraction
sub rd, rs1, rs2

# add immediate
addi rd, rs1, imm
```

由于寄存器十分有限，很多时候我们不得不把数据储存移动到内存(*memory*)

## **Load from** and **Store to** Memory

![processor_memory_graph](processor_memory_graph.png)

- 一般来说数据都是小于$32$ bits的，但是很少会小于$8$ bits，如果是$8$ bits的整数倍可以工作的很好。
- $8$ bit chunk被称为一个字节(*byte*)
	- $1$ word = $4$ bytes
- 内存地址是用*byte*计数的，而不是*word*
- 我们怎么把word存进内存中呢
	- 小端序(*Little-endian convention*)：字的地址和最右端(*LSB: Least Significant Byte*)

## Load from Memory in RISC-V
使用 **Load Word**(`lw`)
in C:
```c
int A[100];
int g = h + A[3];
```

in RISC-V:
```asm
lw x10, 12(x15)
add x11, x12, x10
```
- `x15`: 基址寄存器(*base register*)：指向`A[0]`
- `12`: 地址偏移

## Store to Memory in RISC-V
使用 **Store Word**(`lw`)
in C:
```c
int A[100];
A[10] = h + A[3];
```

in RISC-V:
```asm
lw x10, 12(x15)
add x10, x12, x10
sw x10, 40(x15)
```

## Loading and Storing Bytes
如果我要存的数据没有$32$ bit宽，用`lw`和`sw`就有点浪费
- `lb`: load byte
- `sb`: store byte
```asm
lb x10 3(x11)
```

### Sign extension
如果我们要读取的那个byte他是有符号的呢（**事实上大部分情况是这样的**），如果我们直接把高位的$3$个字节存为$0$，那么不管怎么样它都看起来是正数
这是不对的，那么怎么办？
**直接读取**该字节的RSB，并且扩展到高位的所有字节上

实际上我们有`lbu`，符号扩展就默认是无符号的了

# Decision Making
- RISC-V: *if*-statement instruction is:
```asm
beq reg1, reg2, L1
```
- 如果`reg1`中的值**等于**`reg2`中的值，去编号为`L1`的的语句
	- `beq`: **b**ranch if **eq**ual
	- 类似的我们有`bne`: **b**ranch if **n**ot **e**qual

## Types of Branch
- Branch：改变控制流
- Conditional Branch：基于比较的**结果**改变控制流
	- `beq`和`bne`
	- branch if less than `blt`和branch if greater than or equal `bge`
	- unsigned versions `bltu`和`bgeu`
- Unconditional Branch：总是跳转
	- **j**ump, `j label`

## Loops in Assembly
我们尝试把一个C loop映射到汇编
```c
int A[20];
int sum = 0;
for (int i = 0; i < 20; i++) {
	sum += A[i];
}
```

```asm
add x9, x8, x0
add x10, x0, x0 # sum
add x11, x0, x0 # i
addi x13, x0, 20 # x13
Loop:
bge x11, x13, Done
lw x12, 0(x9)
add x10, x10, x12
addi x9, x9, 4 # &A[i+1]
addi x11, x11, 1
j Loop
Done:
```