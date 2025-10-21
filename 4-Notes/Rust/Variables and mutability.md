默认情况下，rust中的变量是不可修改的(immutable)，如果试图修改，比如：
```rust
fn main() {
	let x = 5;
	println!("The value of x is {x}");
	x = 6;
	println!("The value of x is {x}");
}
```
以上代码会直接报错
```bash
$ cargo run
   Compiling variables v0.1.0 (file:///projects/variables)
error[E0384]: cannot assign twice to immutable variable `x`
 --> src/main.rs:4:5
  |
2 |     let x = 5;
  |         - first assignment to `x`
3 |     println!("The value of x is: {x}");
4 |     x = 6;
  |     ^^^^^ cannot assign twice to immutable variable
  |
help: consider making this binding mutable
  |
2 |     let mut x = 5;
  |         +++

For more information about this error, try `rustc --explain E0384`.
error: could not compile `variables` (bin "variables") due to 1 previous error
```
**小心得**: 注意到 `error` 旁边有一个编号 `E0384`, 遇到不懂的error时可以使用 `rustc --explain E0384` 来获得解释

想要让一个变量能够更改，请加上 `mut` 来显式的声明
```rust
fn main() {
	let mut x = 5;
	println!("The value of x is {x}");
	x = 6;
	println!("The value of x is {x}");
}
```

## Constants
`constant` 是真正意义上的常量，它不允许任何形式的更改，别想要用 `mut` 来试图更改一个常量
我们使用 `const` 关键字来声明一个const变量，并且值得注意的是const的变量类型也需要一起声明
```rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```
记得命名常量的时候要全大写。