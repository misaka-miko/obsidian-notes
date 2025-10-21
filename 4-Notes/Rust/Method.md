# How to define a method
```rust
#[derive(Debug)]
struct Rectangle {
    width: u64,
    height: u64,
}

impl Rectangle {
    fn area(&self) -> u64 {
        self.width * self.height
    }
}

fn main() {
    let rect1 = Rectangle {
        width: 30 * 2,
        height: 50,
    };

    println!("The area of rect1 is {}", rect1.area());
}
```
省流，在 `impl` 的代码块里正常写函数就行，特别的在于，如果你希望它是一个成员方法，第一个参数需要是 `&self` 加上引用是说明不希望莫名失去ownership，如果执意不加 & 说明该对象经过该操作后变为另一对象

# 多参数成员方法？
```rust
impl Rectangle {
    fn area(&self) -> u64 {
        self.width * self.height
    }

    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }
}
```
省流：经典加上other就行，根据方法的实际作用决定是否加上 `mut`

# 无self的函数
我们当然可以不在第一个参数放 `&self` ，这种情况一般用于定义constructor时使用
```rust
    fn square(length: u64) -> Self {
        Self {
            width: length,
            height: length,
        }
    }
```
诶，是不是很熟悉，其实我们之前已经用过很多次了，只是我们没有深究，就是 `String::from()`
这个函数也会返回一个Self，在这个语境就是String对象，同样的，针对我们自己创建的这种方法，我们也是用 `::` 进行调用
```rust
    let squa1 = Rectangle::square(30);
    dbg!(squa1);
```