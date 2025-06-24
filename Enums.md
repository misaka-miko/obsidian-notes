#  怎么定义一个枚举类
非常的简单，只需要加上 `enum` 关键字就行
```rust
enum IPAddrEnum {
	V4,
	V6,
}
```
于是我们得到了一个和Cpp里很像的枚举类，注意是枚举类，这些枚举类型是被限制在你枚举类的命名空间里的，也就是需要加上 `::` 进行访问。
我们可以这么写
```rust
struct IPAddr {
	kind: IPAddrEnum,
	address: String,
}
```
我们当然可以这么写，这非常cpp，那么作为rust programmer，我们应该充分利用rust给我们提供的便利
```rust
enum IpAddr {
	V4(u8, u8, u8, u8),
	V6(String),
}
```
rust中的枚举类允许我们给每一个variant绑定特定的数据，这是没必要一致的，看本身的实现就行，这个则是直接用strcut做不到的。
当然标准库里是实现了IPAddr这个类的，当然他的实现是这样的
```rust
struct IpV4Addr {
// something
}

struct IpV6Addr {
// something
}

enum IpAddr {
	V4(IpV4Addr),
	V6(IpV6Addr),
}

```
难道rust的枚举类会止步于此吗？答案是否定的，我们甚至可以定义一些方法

# Methods in Enum
```rust
#[derive(Debug)]
enum Message {
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}

impl Message {
    fn call(&self) {
        // do something
    }
}
```
**补充** 其实 `enum` 内部的每一个 variant 我觉得你完全可以认为是一个没有struct关键字的结构体，非常的巧合，以上例子正好包含了我们声明结构体的三种方法

定义了方法后你也可以理所当然的去调用
```rust
    move_message.call();
```

# Option 
特别的，rust还有一个定义在标准库里的枚举类 `Option` 
```rust
enum Option<T> {
	None,
	Some(T),
}
```
由于 `Option` 非常好用，它被包括在 prelude中，你不需要显式的call它的namespace
```rust
    let some_number = Some(5);
    let some_char = Some('e');

    let absent_number: Option<i32> = None;
```
Option这个枚举类给我们什么启示？
A：有Option类型的变量是有可能为None值的，我们需要handle这种情况，我们要显式的处理 `Some(T)` 和 `None` 不然编译器会报错