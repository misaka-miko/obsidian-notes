假如你声明了另一个变量但是名字和之前的一个变量一样，会发生什么？
答案是触发 `移动` , 原先变量的所有资源都被转移到了之后的变量上。

**怎么触发shadowing呢** : 很简单，使用 `let` 关键字就可以了
```rust
fn main() {
	let x = 5;

	let x = x + 1;
	{
		let x = x * 2;
		println!("The value of x in the inner scope is: {x}");
	}
	println!("The value of x is: {x}");
}
```

## shadowing verses mut
`let` 非常高效，通过 `let` 触发shadowing我们甚至可以直接修改原本变量的类型，而且如果我们想要用shadowing来重新赋值而忘记了 `let` 关键字我们还会得到一个 compile-time error，非常安全: ）