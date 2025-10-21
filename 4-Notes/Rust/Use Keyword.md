省流：`use`有如下特性
- `use`搞出来的path shortcut只会在当前层级生效，如果你在子模块中试图用在父模块中定义的shortcut会报错
- 我记得`use`是可以直接把函数带入命名空间的，但为什么我看别人不会这么写
	- 对于函数，我们只会把它的父模块引入，目的是为了知道当前函数的来源
	- 对于结构体，枚举类，我们会直接把它们引入，但是如果两个结构体名字一样，比如 `Result` 在 `std::io` 和 `std::fmt` 中都有定义，我们就只能引入他们的父模块，而不是直接引入

针对结构体名字一样的情况我们还可以有这种解决方法
```rust
use std::fmt::Result;
use std::io::Result as IoResult;

fn function1() -> Result {
    // --snip--
}

fn function2() -> IoResult<()> {
    // --snip--
}
```
