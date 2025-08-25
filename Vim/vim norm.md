# Same operation on multiple lines
有时候我们想要对很多行文本实行相同的操作，比如：
- html link
- 修改缩进
- 统一添加某个tag
- ...

怎么做这样的操作呢，事实上在 `vim` 中有非常多的方式
- 你可以用 `macro` 
- 你也可以 原地写一个 `map` 
- 你可以使用 `norm` 
	- 进入 `visual mode` 选中批量处理的文本
	- 进入 `command mode` 你可以看见 `:<,'>` 
	- 输入 `norm <normal mode command>` 来批量处理

**That's it! : )**

[[vim tricks]]