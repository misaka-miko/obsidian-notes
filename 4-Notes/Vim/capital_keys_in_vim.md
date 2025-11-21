---
tags:
  - knowledge
  - vim
---
你总是可以在vim中找到更**高效**的快捷键
- 一般来说我们想要删除当前位置到当前行末可以使用 `norm d$` 但并不好打，请用 `norm D`（norm代表这是normal mode command）
- 类似的 `norm C` 可以做到类似的事情
-  `norm J` 可以把后一行的内容追加到当前行末
-  `norm K` 在没有任何插件的情况下会打开光标下的文字的文档
	- 比如当你hover到Vim上并且使用 `norm K` 可以打开 `man vim`