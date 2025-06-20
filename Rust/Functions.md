怎么声明一个function？使用 `fn` 关键字
怎么命名？所有的字母都应该小写，用 _ 分割
```rust
fn another_function() {
	println!("Another function.");
}
```
值得注意的一点是rust不在乎函数声明的位置，只有声明了就可以被正常调用

## Parameter
如果我要往函数内部传入参数，该怎么办
```rust
fn main() {
    another_function(5);
}

fn another_function(x: i32) {
    println!("The value of x is {x}");
}
```
别忘记声明参数的类型，虽然linter会提醒你

## statement and expressions
rust是一个expression-based的语言那么statement和expression有什么区别
- **statement** 是不会返回值的并且执行特定行为的语句
- **expression** 会得到特定的值
比如这个情况
```rust
fn main() {
	let x = (let y = 6);
}
```
这种奇葩操作是不被允许的，不同于C，这种赋值的语句并不会有返回值，其本身属于 statement，是函数定义的一部分，无返回值。

但如果我就是要达到类似的效果呢
```rust
fn main() {
	let y = {
		let x = 3;
		x + 1
	}
}
```
有如下特性
```rust
{
	let x = 3;
	x + 1
}
```
这个code block可以evaluate出4，注意 `x + 1`后并没有 `;`

## function return value
怎么声明一个函数的返回值
```rust
fn five() -> i32 {
	5
}
```