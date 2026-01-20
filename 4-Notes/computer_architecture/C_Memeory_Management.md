---
tags:
  - knowledge
category: computer architecture
topic: language basics
author: misaka
date: 2026-01-20
---
# C内存管理

本篇笔记记录了一些关于C内存管理的内容

## Dynamic Memory

> If you want it, then you have to take it.

在C中内存管理的轻量化意味着你需要**手动管理**：
- `malloc`：在堆上“开辟”内存，并返回对应的指针，如果失败则返回 `NULL`
- `free`：释放之前使用 `malloc`, `realloc`获取的内存
	- 不要*double free*
	- 不要访问释放过的指针：*use after free*

## Memory Structure

C语言的内存占用由以下几个部分组成
- Code：代码本身的占用 $\to$ **系统管理**
- Static Storage：全局变量 $\to$ **系统管理**
- Stack：局部变量，返回地址(*return address*)，参数 $\to$ **系统管理**
- Heap：动态内存 $\to$ **用户管理**

![C Memory layout](Memory-Layout-of-C-Program.webp)

### Stack
C程序的 *stack* 是由一系列的 *stack frame*组成的，包含
- return address：告诉 stack pointer 待会儿回到哪里
- 参数
- 局部变量

特点：
- 向下增长
- 连续内存
- 如果请求的内存过大直接导致程序崩溃：**Stack Overflow**
- 当 stack frame 被*弹出*时，其中的变量并不会立刻被销毁：
	- 如果接下来没有任何函数调用，很有可能你还是可以访问到其中的变量
	- **WARNING**：永远不要试图在你的程序里这样做，编译器没有义务保证你的这种操作成功

### Heap
堆上的内存并不保证是连续的，比如你连续 `malloc`了两块内存，然后 `free`了前面的那块，内存就会被分成两块
技术上来说，一块内存会有这两个*field*：
- block size
- 指向下一块内存的指针

所有 *free blocks* 都用一个循环链表保存，一块被分配了的内存指针*field*未被使用：如果未被正确保存，后续就没有办法释放了 $\to$ **memory leak**

基于这种想法，我们可以这样看待 `malloc`和`free`：
- `malloc`：从 free memory list中访问一块足够大的内存，如果没找到，则向系统要求分配一块更大的内存，如果失败返回 `NULL`
	- best fit：有点慢
	- first fit：很可能导致链表前方有很多分散的内存(*fragment*)
	- next fit：采取first fit，但是下一次查询从当前分配位置开始查询，分散*fragment*
- `free`：检查相邻的内存是否为free
	- 如果是，那么合并
	- 否则，把这块内存加入链表