# if expressions
rust的控制流语句
```rust
fn main() {
	let number = 3;

	if number < 5 {
		println!("condition was true");
	} else {
		println!("condition was false");
	}
}
```
 值得注意的是，条件语句的值必须要是bool类型的，不然就会直接抛出error
 PS: 别写试图C style : )

# 多条件
```rust
fn main() {
	let number = 6;

	if number % 4 == 0 {
		println!("number is divisible by 4");
	} else if number % 3 == 0 {
		println!("number is divisible by 3");
	} else if number % 2 == 0 {
		println!("number is divisible by 2");
	} else {
		println!("number is not divisible by 4, 3, or 2");
	}
}
```
非必要情况用太多的else if会让你的code很恶心，请使用match

# if 参与的赋值
由于 `if` 本身属于expression，可以放在let赋值的右端，可以实现类似三目运算符的效果
```rust
fn main() {
	let cond = true;
	let number = if cond { 5 } else { 6 };
	println!("The value of number is {number}");
}
```
但是在使用这个特性的时候请注意，if expression的值取决于哪一个code block被执行，也就是说有可能性被执行的code block中得到的最终结果必须是相同类型的。


# 循环语句
rust有三种循环语句 `loop`, `while` , `for`

## loop
`loop` 循环会使程序不断重复，知道用户打断，或者break语句
```rust
loop {
	println!("again");
}
```

### 从循环中返回值
到底什么时候用loop
A：如果你需要重复尝试一个很可能失败的命令，比如你想要检查某一个线程的工作有没有完成，你可能还想要把那个操作的结果给返回出来，那么你可以这么做
```rust
fn main() {
	let mut counter = 0;
	let result = loop {
		counter += 1;
		if counter == 10 {
			break counter * 2;
		}
	}
	println!("the result is {result}");
}
```

### break & continue 的返回位置
在大部分的编程语言中，有这样一个痛点，break和continue往往只能针对最内层循环，如果我们希望指定break和continue的位置怎么办呢
rust中你可以通过添加一个*循环标签* 来解决这个问题，循环标签开始于一个引用(quote)符号
```rust
fn main() {
	let mut count: u32 = 0;
	`counting_up: loop {
		println("count = {count}");
		let mut remaining = 10;

		loop {
			println!("remaining = {remaining}");
			if remaining == 9 {
				break;
			}
			if count == 2 {
				break `counting_up;
			}
			remaining -= 1;
		}
		count += 1;
	}
	println!("End count = {count}");
}
```

## while
其实我认为while或者for其实已经足够cover大多数的情况了，那么我们怎么写while loop呢
```rust
fn main() {
	let mut number = 3;
	while number != 0 {
		println!("{number}!");
		number -= 1;
	}
	println!("Genshin, QiDong!");
}
```

## for loop
问题又回到了经典的如何遍历容器，难道要用while循环加下标的方式去遍历吗，这种方式是非常**不明智**的，如果你后来要改变array的大小，但是却忘了更改你的loop condition，所以我们有更好用的for，类似于python和cpp的for each loop，我们可以简单的这么写
```rust
fn main() {
	let a = [10, 20, 30, 40, 50];
	for element in a {
		println!("the value is: {element}");
	}
}
```
what's more,我们甚至还有for range loop
```rust
fn main() {
	for number in (1..4).rev() {
		println!("{number}!");
	}
	println!("Genshin, QiDong!");
}
```