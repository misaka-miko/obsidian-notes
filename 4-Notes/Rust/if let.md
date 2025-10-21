# if let
有时候我们可能并没有想要匹配非常多的可能性，比如说对于一个 `Option` 我们可能只希望对 `Some(T)` 去处理，rust提供了 `if let` 语法糖
```rust
let config_max = Some(3u8);
if let Some(max) = config_max {
	println!("The maximum is configed to be {max}");
}
```
这个语法糖可以达到和match类似的效果，但是代码结构更清晰，但是代价是什么？
A：编译器没有办法进行完备性检测，可能会导致bug
当然我们if let也可以加上else分支，但是个人觉得那我为什么不用match呢？

# let else
**NOTE:** 目前这里的理解可能不够准确，后续有待调整
我们可能会遇到这种情况，代码的某一分支是非常复杂的，但是另一分支（可能作为某种错误处理的分支）逻辑比较清晰，我们可以使用 `let ... else` 来处理这种情况
```rust
fn describe_state_quarter(coin: Coin) -> Option<String> {
    let Coin::Quarter(state) = coin else {
        return None;
    };
    if state.existed_in(1900) {
        Some(format!("{state:?} is pretty old, for America!"))
    } else {
        Some(format!("{state:?} is rather new"))
    }
}
```
值得注意的是，let else会把state绑定到外部作用域，允许我们后续处理复杂分支，但是if let没有这种特性，绑定的变量名仅限于内部作用域

