省流： `use` 关键字可以引入某个模块的函数，结构体等等
`pub` 关键字可以让其他模块正常访问被标记的代码

# Modules Cheat Sheet
模块是怎么工作的
- **从根模块开始** ：编译器最先找的是 `src/main.rs` 和 `src/lib.rs`
- **声明模块** ：用 `mod` 关键字，比如 `mod garden`，编译器会去这几个目录找定义
	- Inline, 也就是 `mod garden {}` 里的内容
	- `src/garden.rs`
	- `src/garden/mod.rs`
- **声明子模块** ：比如 `mod vegetable` ，编译器会去以下几个地点找定义
	- Inline, 同上
	- `src/garden/vegetable.rs`
	- `src/garden/vegetable/mod.rs`
- **路径**: 省流，类似于文件目录结构，根目录是 `crate`,比如有 `Asparagus` 在 garden vegetables 可以在这里找到 `crate::garden::vegetables::Asparagus`.
- **访问控制**: 子模块默认是private的 ,显式声明`pub mod` 而不是`mod`. 让模块内的内容可见, 用`pub` .
- **`use` 关键字**: 省流，用use加绝对路径引入可以少许写点东西 ,比如之前的那个结构体，引入后只用写`Asparagus` 就行。

