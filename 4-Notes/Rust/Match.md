*related note*:
[[if let]]
省流， `match` 就是 rust 版的 switch-case，但是有更多feature

# Match Enum
```rust
enum Character {
    ThreeStar,
    TwoStar,
    OneStar,
}

impl Character {
    fn value_in_character(&self) -> u32 {
        match self {
            Character::OneStar => 1,
            Character::TwoStar => 10,
            Character::ThreeStar => {
                println!("出金啦恭喜");
                50
            }
        }
    }
}
```
回顾之前讨论enum的用法，我们知道可以给特定的variant绑定相关的数据，但是我们没有说怎么用，match就给我们提供了一个方式来提取绑定的数据
```rust
#[derive(Debug)] // so we can inspect the state in a minute
enum UsState {
    Alabama,
    Alaska,
    // --snip--
}
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),
}
fn value_in_cents(coin: Coin) -> u8 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter(state) => {
            println!("State quarter from {state:?}!");
            25
        }
    }
}
```

# Match Option
还记得我们之前说的Option吗，我们现在也可以提取 `Some(T)` 进行使用了
```rust
fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        Some(i) => Some(i + 1),
        None => {
            println!("nothing to add!");
            None
        }
    }
}
```

# Catch all
回到整型数据，我们有时并不想手动去写所有其他的情况，这时候可以用other来catch all，类似于default，这时候其他值被other绑定
```rust
    let dice_roll = 9;
    match dice_roll {
        3 => add_fancy_hat(),
        7 => remove_fancy_hat(),
        other => move_player(other),
    }

    fn add_fancy_hat() {}
    fn remove_fancy_hat() {}
    fn move_player(num_spaces: u8) {}
```
如果我们不希望绑定其他值呢，我们可能什么都不想做，那就用 `_`
```rust
    let dice_roll = 9;
    match dice_roll {
        3 => add_fancy_hat(),
        7 => remove_fancy_hat(),
        _ => (),
    }

    fn add_fancy_hat() {}
    fn remove_fancy_hat() {}
```
