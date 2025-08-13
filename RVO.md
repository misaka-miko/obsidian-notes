# What is RVO?
- `RVO` : 是 **Return Value Optimization** 的缩写
- `RVO` 所干的事就是允许直接在接收对象的内存位置构造返回值
- `RVO` 的实现是 `implementation defined`。To be more detailed:
	- 在 `cpp98` 之后，编译器可以实现 `URVO` (I' ll cover it later) 
	- 在 `cpp17` 之后，编译器被要求实现 `URVO`
	- `NRVO` 的实现是 `optional` 的，但是推荐实现

*show up case*:
```cpp
class MyObj {
/* some implementation */
}

MyObj do_something() {
	MyObj a;
	return a;
}

int main() {
	MyObj e1 = do_something();
	return 0;
}
```
上述代码中，理论上有 一次构造加两次拷贝，开启 `RVO` 编译器会直接在`e1`处原地构造 `MyObj`

# Types of RVO

## NRVO
```cpp
void do_something() {
	MyObj a(3);
	return a;
}
```

## (U)RVO
```cpp 
void do_something() {
	return MyObj(3);
}
```

**SOMETHING Evil**: 正如我们之前提到的，`RVO`，尤其是 `NRVO` 只是编译器可以选择的feature，我们可以通过 `-fno-elide-constructors`这个编译选项关掉 `RVO` 优化

# When NO `RVO`？

- With flag `-fno-elide-constructors` 
- 返回值的 `constructor` 在当前scope之外调用
- 返回值和返回的类型不一致
- 多个 `return statement` 返回不同的对象（仅对`NRVO`而言）
-  返回一个复杂的 `expression` （仅对`NRVO`而言）
- 当拷贝构造函数和移动构造函数不存在时
	- `NRVO` 无法成功编译
	- `URVO` works fine :)