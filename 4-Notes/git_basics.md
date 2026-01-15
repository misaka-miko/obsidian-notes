---
tags:
  - knowledge
  - git
---
# Git Basics

在这个笔记中我们会涵盖基本的 `git` 用法，这些用法基本上会跟随你的 `git` 使用生涯。

## Initializing a Git Repository

你有两种办法创建一个 `git` 仓库
- 初始化一个本地文件夹
	- `cd <target-directory>`
	- `git init`
- 克隆一个远程仓库
	- `git clone <remote-url/ssh>`
	- 使用 [github-cli](https://github.com/cli/cli)

**NOTE**: 你可以指定 `git clone` 后的项目文件夹名：
```bash
git clone <url> <dir-name>
```

## Checking the Status of Your Files

在没有任何图形化或者终端图形化的工具的情况下，我们应该怎么样查看当前仓库的状态？介绍： `git status`。
事实上，如果你选择纯命令行 `git`， `git status` 是你最好的伙伴，在你不确定当前 `git` 的状态，请**立刻运行** `git status`。
当你克隆了一个仓库之后运行这个命令一般会得到如下输出
```bash
git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
```

**NOTE**: 现在Github的默认分支名是 `main`。你可以在 `.gitconfig` 里修改默认分支名来同步。

你可以使用 `git status -s` 来获取精简版的状态信息。

## Tracking New Files

现在你做出了一些更改，你希望 `git` 开始追踪它，你只需要使用：

```bash
git add <filename>
```

就可以 `stage` 这个文件了，但是粗心的你发现你选择错了，你想要 `unstage` 这个文件：

```bash
git restore --staged <filename>
```

如果你对 `stage` 过的文件再次更改，你会发现它会同时出现在 `staged file` 和 `modified file` 中，你需要再次运行 `git add <filename>` 追踪最新版本的文件。