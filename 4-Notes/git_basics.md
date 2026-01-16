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
如果你比较懒，想要直接把当前working tree中的所有文件全部追踪，运行：

```bash
git add .
```

## Ignoring Files

事实上有时候我们根本不想要处理是否提交某个文件，比如说
- 编译产生的 object file 
- 自动生成的文档
- 某些日志文件
- $\dots$

我们可以添加一个 `.gitignore` 文件来告诉git我们不想要跟踪哪些文件
```bash
cat .gitignore
*.[oa]
*~
```
`.gitignore`的规则如下
- 空行和用`#`开始的行将会被忽略
- *standard glob patterns*用来匹配特定的文件，并且会在 working tree下递归调用
	- 在匹配句式前加 `/` 可以避免递归调用
	- 在匹配句式后加 `/` 以声明这是一个文件夹
- 在特定模式前加 `!` 以排除对该文件的忽略

关于glob pattern，请参考[[Regex]]
想要看一些gitignore案例，请访问[该网站](https://github.com/github/gitignore)

## Viewing Your Staged and Unstaged Changes

怎么看我对文件内部具体做了哪些更改：
- `git diff`：查看有哪些 unstaged hunk
- `git diff --cached/--staged`：查看相比上一次提交有哪些变更

## Commit Your Changes

当你决定哪些文件可以进入你的下一次变更，你可以运行 `git commit` 进行提交，具体来说：
- `git commit`：打开默认的编辑器写 *commit message*
- `git commit -m <message>`：对于简短的提交信息这么做也可以
- `git commit -v`：给你的编辑器提供 `git diff` 的输出
- `git commit -a`：自动stage已经**追踪过的**文件，**不建议使用**

## Remove Files

很多git初学者只会提交文件但是一旦提交错了文件就傻了，事实上这是不必要的，git提供了很方便的删除功能：
- `git rm <filename>`：直接删除该文件并且不再追踪该文件
- `git rm --cached <filename>`：停止追踪该文件，但是不会实际删除这个文件，一般用于漏写 `.gitignore` 的情况，**非常好用**

## Move Files

当我们给一个文件重命名，git会这么认为用户的行为
1. 删除一个原文件： `git rm <file-from>`
2. 添加一个新文件，内容和原文件一样，名字不一样： `git add <file-to>`

git提供了更方便的做法：
```bash
git mv file_from file_to
```

## Viewing the Commit History

git提供了非常强大的工具 `git log` 来帮助我们查看提交记录，它所做的最基本的事情就是列出当前分支的所有提交和提交信息，当然不止如此：
- `git log -p/--patch`：为每个commit增加了相应的 `diff`，代码审查的时候非常好用
	- `-<number>`可以指定你要看多少条提交信息，比如 `git log -p -2`
- `git log --stat`：提供每次提交的缩略文件变更数和各个文件内部的增添数
- `git log --pretty=<prebuilt type>`：支持不同风格的输出
	- `git log --pretty-oneline`：将每个提交信息精简为$1$行
	- `short`, `full`, `fuller` etc.
	- `git log --pretty=format:"<format string>"`：支持自定义输出格式，比如你要写个调用 `git log`的程序，你希望更高效的解析它的输出，你就可以这么做，比如：
```bash
git log --pretty=format:"%h - %an, %ar : %s"
47753f9 - misaka, 19 hours ago : clean: remove test jupyter
3f64880 - misaka, 20 hours ago : feat!: add jupyter file for percolation
7652ef2 - misaka, 3 weeks ago : docs: add docstring to PercolationStats
17577cd - misaka, 3 weeks ago : feat!: add statistics class for percolation model
6a3744b - misaka, 3 weeks ago : chore: ignore __pycache__/
bf34a65 - misaka, 3 weeks ago : docs: add docstring to percolation class
78ceff3 - misaka, 3 weeks ago : fix: stop tracking test files
f4d1b2d - misaka, 3 weeks ago : feat!: build percolation class to simulate the process
9901a0c - misaka, 3 weeks ago : chore: ignore some test file
45efb12 - misaka, 4 weeks ago : test: add test
```

## Limiting Log Output

大部分时候我们并不希望有完整的提交日志，我们可以通过以下方法筛选
- `git log -<n>`：显示前$n$条提交记录
- `git log --since/--until=<date>`：按时间筛选 
- `git log --author=<author-name>`：按作者筛选
- `git log -- <path/to/file>`：筛选出对特定文件有更改的提交