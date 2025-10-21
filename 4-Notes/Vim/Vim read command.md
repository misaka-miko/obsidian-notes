---
tags:
  - knowledge
  - vim
---
# 如何将一条命令的输出快速写入vim
A: 使用 `:read ! <command>` ，可以实现vim下的输出重定向（类似在终端下是使用 `<command> > <file_to_read>`） 
**值得注意的是**：vim的 `:read !` 调用的是系统的默认shell，而不是当前用户的shell，不要指望他可以兼容 `fish` 语法 : ( 

---
# `:read` 还可以怎么用
使用 `:read /path/to/your/file` 可以将另一个文件的内容输出到当前文件

[[vim tricks]]