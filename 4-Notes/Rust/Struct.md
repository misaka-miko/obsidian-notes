省流，我们有三种方式定义一个Struct， `curly braces` , `tuple`, `empty`
# 花括号初始化
```rust
struct User {
    active: bool,
    email: String,
    username: String,
    sign_in_count: u64,
}
```
大括号声明的struct支持以下两种初始化
```rust
    let user1 = User {
        active: true,
        username: String::from("user123"),
        email: String::from("user1@abc.com"),
        sign_in_count: 1,
    };

    let user2 = User {
        email: String::from("user2@xyz.com"),
        ..user1
    };
```
注意，rust不在乎内部field的初始化顺序
为什么不用 `=` 来给 `user2` 赋值，答案是可能触发移动

---
#  元组初始化
```rust
struct Color(i32, i32, i32);
struct Point(i32, i32, i32);
fn main() {
    let black = Color(0, 0, 0);
    let origin = Point(0, 0, 0);
}
```
要想要访问内部元素的话就用 `.` 加下标
这种元组结构体是支持解包的
```rust
    let Point(x, y, z) = origin;
```

---
# 空结构体
我们也可以不给结构体内部放任何的field
```rust
struct AlwaysEqual;
fn main() {
    let subject = AlwaysEqual;
}
```

---
# Misc
我们是否可以在结构体里塞引用，比如 `&str` ：可以，详情见 lifetime

关于如何将结构体作为函数的参数
A：省流，如果你没有实现 Clone， 那么请传入引用，访问传入引用的结构体内部成员不会move

## 结构体的标准化输出
就好像Cpp一样，我们如果试图使用 `std::cout` 来输出某种复合结构，我们需要对输出流进行重载，类似的，rust中为了能让 `println!` 能知道我们想要怎么输出结构体，我们需要手动实现，或者加上 Debug trait
```rust
#[derive(Debug)]
struct Rectangle {
    width: u64,
    height: u64,
}
fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };
    println!("rect1 is {rect1:#?}");
}
```

