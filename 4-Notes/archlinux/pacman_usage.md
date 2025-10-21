---
tags:
  - archlinux
  - knowledge
---
# 获取版本
- 获取所有显式下载的包的版本 `pacman -Qe`
- 获取所有在`package group`中的包 `pacman -Sg group`
- 获取所有陌生的包（一般都是手动下载的或者是已经被移除的 `repo`） `pacman -Qm`
- 获取所有本地的包 `pacman -Qn`
- 获取所有本地的显式下载的包 `pacman -Qnet`
	- 可以通过这个命令制作一个安装包同步脚本（**安装后**脚本）
- 列出regex的包 `pacman -Qs regex`
	- 关于如何使用 *regular expression*，请参考[[Regex]]

---
# 安装软件
- 最基本的安装 `pacman -S <package name> ...` 
- 通过 *regular expression* 安装 `pacman -S $(pacman -Ssq _package_regex_)`
- 如果一个软件在不同的源中有不同的版本，你可以这样指定版本 `pacman -S extra/<package name>`
- 有时候一个包可能属于一个包群，比如经典 `gnome` `kde` 等桌面环境包，安装时你可以指定安装其中的某些软件包
	- *PS*: 都装DE了还纠结这些干嘛LOL
	- 通过 `pacman -Sg <group name>` 查询包群中的软件包

---
# 卸载软件
- 对于一些孤立包，直接使用 `pacman -R <package-name>` 即可
- 如果要把一些不被其他软件依赖的依赖包一起删掉，使用 `pacman -Rs <package-name>`
- 要无视其他依赖关系，**强行**删除 `pacman -Rsc <package-name>` **不要用这个**