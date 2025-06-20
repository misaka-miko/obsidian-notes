rust中的数据类型可以分为两个子集: `scalar` 和 `compound`
怎么声明一个类型
```rust
let guess: u32 = "42".parse().expect("Not a number!");
```
# scalar types
`scalar` type代表一个值。主要的几种 `scalar` type：integers, floating-point numbers, booleans 和 characters


## Integer type

| length | signed | unsigned |
| ------ | ------ | -------- |
| 8-bit  | i8     | u8       |
| 16-bit | i16    | u16      |
| 32-bit | i32    | u32      |
| 64-bit | i64    | u64      |
| 128bit | i128   | u128     |
| arch   | isize  | usize    |
怎么去写一个整形的字面值

| number literals   | example     |
| ----------------- | ----------- |
| decimal           | 98_222      |
| hex               | oxff        |
| octal             | 0o77        |
| binary            | ob1111_0000 |
| byte( `u8` only ) | ` b`A`  `   |
怎么处理整型溢出
省流，用这四种标准库的方法
- wrapping_*
- return `None` 如果有溢出的 `checked_*` 方法
- `overflowing_*` 返回值和boolean表示是否有溢出
- `saturating_*` 方法

## Floating-Point types
有两种浮点类型: `f32` 和 `f64` ，默认64位，速度差不多的同时提供更高的精度

## Boolean type
```rust
fn main() {
	let t = true;
	let f: bool = false;
}
```

## Character type
```rust
fn main() {
	let c = 'z';
	let z: char = 'z';
	let emoji = 'U+0000';
}
```

# Compound types
rust有两个原生的compound type: tuple 和 array

## tuple
tuple是定长的，声明之后不允许任何的增加和缩减
```rust
fn main() {
	let tup: (i32, f64, u8) = (500, 6.4, 1);
}
```

tuple的声明支持动态类型绑定(编译器足够聪明)，同时还支持解包，访问时也支持下标访问
```rust
fn main() {
	let tup = (500, 6.4, 1);
	let (x, y, z) = tup;
	let fiva_hundred = tup.0;
	let six_point_four = tup.1;
	let one = tup.2;
	println!("The value of y is {y}");
}
```

## array
rust中的array中的数据只能是同一类型的，并且也是定长的（学C学的）

```rust
// array的三种声明方式
fn main() {
	let a = [1, 2, 3, 4, 5];
	let a: [i32; 5] = [1, 2, 3, 4, 5];
	let a = [3; 5];

	let first = a[0];
	let second = a[1];
}
```