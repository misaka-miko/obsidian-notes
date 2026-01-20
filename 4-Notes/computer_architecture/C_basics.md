---
tags:
  - knowledge
category: computer architecture
topic: language basics
author: misaka
date: "2026·Monday: 01/19"
---
# C语言基础
本篇记录一些我认为需要在 `computer architecture` 这门课上需要注意的一些事项

## Integer type

我们需要更加 **ROBUST** 的代码，但是非常不幸的是C中的内置整型 `int` 的大小会根据架构变化，会导致极其难以预测的行为，我们应该怎么办？

**ANSWER**：请使用 `<inttype.h>`

## Bool type
C中并没有直接内置 `bool` 类型，以下几种方式可以表达类似的效果：
- `int` : 0 $\to$  false, 否则为true
- `NULL`：false
- `<stdbool.h>`

## Pre-Processor
C中任何用 `#`开始的代码会被看作是cpu指令，经过 **CPP** 处理后会变为仅可被编译器所见的 `.i` 文件，常见用法如下：
- 头文件保护：`#ifdef`, `#endif`, `ifndef`, $\dots$
- 宏替换
	- **请小心使用**：定义不规范，亲人两行泪

## `Const` Values

为什么你需要**常量**：
- 让你的代码更可读
- 防止错误更改
- 维护简单

常见的手段：
- `const` 关键字
- `#define` 宏
- `enum` 枚举类 (比宏更好)
	- 我喜欢用 `typedef enum {} <alias>`，这样子后续访问枚举类不需要加 `enum`

## Pointer
pointer(*指针*)在C语言中十分重要，为什么你需要使用指针？
- 更轻量的传参
	- 比如需要在一个函数里需要访问一个巨大的结构体，使用值传递显然是不合理的
- 简化代码

一些好玩的用法：
- 熟悉python的用户可能知道python中有 `map` 这个功能，基本上做的事情就是给一个 sequencial object中的所有元素应用一个映射 (function)
	- 这个功能需要接受一个函数作为参数，C语言可以通过函数指针做到这件事：
```c
// How to declare a function pointer
// return_type (*fp) (arg_type); 
int (*fp) (void *, void *) = &foo

// Calling a function pointer
int result = (*fp)(x, y)
```

**WARNING**：事实上，虽然pointer很好用，但是也同样很危险
- 比如解引用 `NULL` 或者访问 `NULL`都是非法的
- **Segmentation fault**：比如你试图解引用一个*未初始化的*(uninitialized)指针，很有可能试图访问没有读写权限的内存导致的错误
- **Bus errors**：一般当指针没有*字对齐*(word-aligned)，会产生这个错误