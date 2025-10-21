问题来到了我们应该怎么找到模块中对应的函数，结构体，枚举类呢
我们之前以前提到了我们可以用 `crate::module_name::submodule_name...` 的形式来找到对应的代码
当然我们还有其他办法，也就是*相对路径* 
```rust
mod front_house {
	pub mod hosting {
		pub fn add_to_waitlist() {}
	}
}

pub fn eat_at_restaurant() {
	crate::front_house::hosting::add_to_waitlist();
	
	front_house::hosting::add_to_waitlist();
	
}
```
相对路径：定义在相同层级中的模块作为起始路径
需要注意的点：
- 我们需不需要用 `pub` 关键字让 `eat_at_restaurant` 可以看见 `front_house` ？
	- 其实不需要，因为他们被定义在同一层级，称作 `siblings` ，互相之前是可见的
- 一个函数或者其他的代码块只有加上了 `pub` 关键字才能被它的 `parent mod` 看见，即可被使用。

# Best Practise
我们之前说过，我们其实可以同时有 `main.rs` 和 `lib.rs`。我们所有的public的内容应该放在 `lib.rs` 中， `main.rs` 应该作为你的包的使用者

# Super Keyword
如果一个模块内有一个方法是依赖于父类中的某个方法，比如一个餐厅，出餐应该是restaurant这个副模块管理的，但是我的 `back_house` 模块可能有一个 `fix_incorrect_order` ，但是它不应该自己管理出餐，而是应该寻求它的父模块，其实就是 `back_house` 来管理，它可以这么调用。在 `src/lib.rs`中
```rust
fn deliver_order() {}

mod back_house {
	fn fix_incorrect_order() {
		super::deliver_order();
	}
}
```

# pub for Struct and Enum
省流：如果你pub了一个结构体，它内部的field仍然是private的，我们仍然需要 `pub` 来显式声明可见性。但是pub一个枚举类，你会把它所有的varient给都`pub`