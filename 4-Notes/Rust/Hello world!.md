# 你的第一个rust程序
in your main.rs
```rust
fn main() {
	println!("hello world!!");
}
```

## 如何运行
一般来说你应该使用cargo，但如果你只希望单独编译一个rust程序，请使用 `rustc`
```bash
rustc main.rs
./main
```

## 一些解释
```rust
fn main() {

}
```
main函数在rust中是特别的，它永远是一个rust程序中第一个运行的函数，*其实就是程序的入口*, 如果需要接受参数就写在括号里。

```rust
println!("hello world!!");
```
`println!` 会调用rust的宏(macro)，如果调用同名的函数你应该写`println`