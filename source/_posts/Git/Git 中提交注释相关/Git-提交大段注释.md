---
title: Git 中提交一大段、多行的注释
toc: true
---

如果要添加大段注释，必须要调用文本编辑器。可以使用 `core.editor` 选项来修改默认的编辑器[^1]。

## 具体配置

### 两大编辑器

```shell
$ git config --global core.editor emacs
$ git config --global core.editor vim
```

注意： mac 下，指定 vim 提交时，在文本编辑界面，命令模式要使用英文输入法才能响应（如果使用中文输入法敲命令，会报警，还会插入命令的字符）

### 其他编辑器

```shell
$ git config --global core.editor "[your editor] -w"
```

`-w` 通知 Git 使用其他的指定编辑器

##### macvim

用 macvim 做commit时的编辑器，用 `-f`参数能避免下面的提示。（`-w` 参数无效）

> Aborting commit due to empty commit message.

在终端修改 git config 如下：

```shell
git config --global core.editor "/bin/mvim -f"
```

## 使用方法

使用 `git commit` 调用

例子：

```shell
touch README.md
git init
git add README.md
# git commit -m "first commit" # 命令行添加提交信息
git commit # 编辑器添加提交信息
```

## 参考

[^1]: [Git - 配置 Git # core.editor](https://git-scm.com/book/zh/v2/%E8%87%AA%E5%AE%9A%E4%B9%89-Git-%E9%85%8D%E7%BD%AE-Git)

