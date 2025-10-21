省流，当你运行 `cargo new my_project` 时，你的package信息被存放在 `Cargo.toml` 中
一个项目可以有多个 binary crate，但是只能有一个 library crate，默认的 binary crate 是 `src/main.rs`
默认的 library crate 在scr/lib.rs，值得注意的是lib.rs内部不能有 `main`
其余的crate应该在 `src/bin/`

[[Control Scope and Privacy]]