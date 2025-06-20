所以什么是ownership，其实就是rust管理内存的手段

# Stack & Heap
什么是栈（stack）?栈的结构是**后进先出**，一个现实中的例子，你有一堆盘子，先叠的在最下方，意味着最后拿出。但是栈上的数据必须要有固定的已知的大小，直接对栈中间的数据操作是不合法的。如果你需要一个运行时确定的数据，你需要将其开在堆（heap）上。

heap的结构更为松散，你可能会向堆请求一定大小的空间，memory allocator会找一块足够大的空闲空间，标记为正在使用，并且返回一个指针指向这块空间，而这个指针拥有确定的大小，会被存放在栈上。

**ownership**就是帮助用户来管理heap data的系统。
- 每一个value都有一个owner
- 同时只能存在一个owner
- owner出了作用域（scope），value将会被丢掉(dropped)

# Scope
```rust
{ // s is not valid here, it's not yet declared
	let s = "hello"; // s is valid from this point forward
} // the scope is now over and s is no longer valid
```

# String type
字符串字面值是不够的，如果我们想要从用户那里获取输入的字符串呢，于是我们引入 `String` 类型来处理开辟在heap上的字符串，我们可以从一个string literal创建一个String
```rust
	let s = String::from("hello");
```
同样的，我们也可以让s变成可以修改的
```rust
	let mut s = String::from("hello");
	s.push_str(", world");
	println!("{s}");
```
当这个s出了scope，rust会自动调用drop函数返回堆上的内存

# Variables and Data Interacting with Move
```rust
	let x = 5;
	let y = x;
```
这个情况是很简单的，但是如果x的数据是在堆上的呢？
```rust
	let s1 = String::from("hello");
	let s2 = s1;
```
省流，rust并不会shallow copy，而是直接移动s1的资源给s2，s1的资源会无法被访问。

# Scope and Assignment
```rust
	let mut s = String::from("hello");
	s = String::from("aboy");
```
省流，当我们创建一个新的字符串aboy并且赋值给s时，原本的hello由于没有任何变量指向它而立刻out of scope，被调用drop函数

# Clone
如果我就是要复制deep copy一个字符串呢
```rust
	let s1 = String::from("hello");
	let s2 = s1.clone();
```

# Function parameter
省流，我们往函数内传入参数的时候也会触发copy或者move，特别的如果我们往函数内传入或者返回`String` 我们就会触发move，但这个有时是很恶心的，如果我们只希望函数使用而不获得所有权怎么办呢，我们函数内的结果可能也需要返回，于是rust很贴心的允许了返回元组，我们也可以用解包很简单的得到里面的值
```rust
fn main() {
	let s1 = String::from("hello");
	let (s2, len) = calculate_length(s1);
}

fn calculate_length(s: String) -> (String, usize) {
	let length = s.len();
	(s, length)
}
```

