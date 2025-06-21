我们知道rust设计到函数传参时，如果传入的type定义了drop，那么直接传入就会导致原本的变量失去所有权，非常的麻烦，事实上大部分情况我们都希望保留所有权，那么这时候就到引用的场景
```rust
fn main() {
	let s1 = String::from("hello");
	let len = calculate_length(&s1);
}

fn calculate_length(s: &String) -> usize {
	s.len()
}
```
`&s1` 创建了一个 `s1` 的引用，但是引用对一个变量没有所有权

# mutable references
如果我想要在函数内部进行修改呢，请加上mut关键字
```rust
fn main() {
    let mut s = String::from("hello");
    change(&mut s);
}

fn change(some_string: &mut String) {
    some_string.push_str(", world");
}
```
注意，你不能用一个可变引用绑定一个不可变变量，反之可以，但会给出一个warning
并且可变引用同时只能存在一个

省流，你不可以有超过一个的可变应用，更加苛刻的是，你如果有不可变引用，那么你也不能绑定可变引用

那么什么时候我们可以引入第二个可变引用呢

## reference scope
引用的作用域开始于它被创建的时候，结束于它第一次被使用，因此这种请况是对的
```rust
let r1 = &s;
let r2 = &s;
println!("{r1} {r2}");
let r3 = &mut s;
```