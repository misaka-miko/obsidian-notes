# 什么是Cargo
简单来说，cargo就是rust的构建系统和包管理器，非常好用所以请务必使用
**检查你是否有cargo和版本**
```bash
cargo --version
```

# 用Cargo创建一个新项目
你可以使用如下命令创建一个项目
```bash
cargo new hello_cargo
cd hello_cargo
```
cargo默认的版本控制工具是git

# Cargo的配置文件
当你创建好了你的项目时，你可以看到一个 `Cargo.toml` 文件，这里控制你的依赖版本
```toml
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2024"

[dependencies]
```
如果你一开始没有用cargo管理，你也可以之后用 `cargo init` 来创建，学git学的:(

# 怎么运行
用 `cargo build` 构建， `./target/debug/hello_cargo` 运行
省流 直接用 `cargo run` 就能一键编译运行
如果是为了release那么就加个flag `cargo build --release`