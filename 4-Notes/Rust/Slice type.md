想想一下这个场景，我们想要写一个函数，返回一个字符串中的第一个单词
```rust
fn first_word(s: String) -> usize {
	let bytes = s.as_bytes();
	for (i, &item) in bytes.iter().enumerate() {
		if itme == b' ' {
			return i;
		}
	}
	s.len()
}
```
我们需要遍历字符串中的每一个字母来确认是否为空格
```rust
	let bytes = s.as_bytes();
```
`as_bytes`方法可以把字符串变成bytes的数组
```rust
	for (i, &item) in bytes.iter().enumerate() {
```
此处的iter方法会把一个容器中的每一个元素返回出来，而enumerate可以把iter返回的结果打包，返回出来一个个元组，第一个元素是index第二个元素是iter返回出来元素的引用

*看起来好像没什么问题* ，但是如果原本的字符串是一个mut的对象，并且我已经做出了breaking change，比如清空了，这时候返回出来的值是没有办法被同步的

# String slice
```rust
let s = String::from("hello world");
let hello = &s[0..5];
let world = &s[6..11];
```
值得注意的是如果从开始位置创建slice，那么0可以省略，类似的，如果包含最后一个byte，那么..的右端也可以省略
所以之前的代码也可以这么写
```rust
fn first_word(s: &String) -> &str {
	let bytes = s.as_bytes();
	for (i, &item) in bytes.iter().enumerate() {
		if item == b' ' {
			return &s[..i];
		}
	}
	&s[..]
}
```
PS： 一个误区，我能不能把返回值写成 `s`？答案是不行，请仔细查看函数签名，返回值是一个字符串字面值的引用，而s是字符串的引用，签名是不一致的，这个甚至rust compiler不会报错，非常隐形的错误
还有就是请放心的用这个函数给外部变量赋值，永远注意，我们切片的字符串属于外界，而不是local variable，因此reference不会失效

# String Literals as Slices
```rust
	let s = "hello world";
```
这里s的类型是 `&str`

# String Slices as Parameters
我们之前的函数是可以优化的，我们可以修改函数的签名
```rust
fn first_word(s: &str) -> &str {
```
为什么这么改？因为这同时让我们可以在 `&String` 和 `&str`  上使用这个函数


