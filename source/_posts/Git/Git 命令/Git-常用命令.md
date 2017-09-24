---
title: Git 常用命令
toc: true
---

如下是个人较常用或一些没有百分百记住的命令，附有 alias (别名)[^1]

## 查看改变

```shell
$ git diff <filename>
$ g d <filename>
```

## 提交注释

### 提交一行注释

```shell
$ git commit -m 'your-comment'
$ gcmsg 'your-comment'
```

### 编辑器提交多行注释

```shell
$ git commit # 设置好后，会进入相应编辑器
```

## 分支操作

### （新建并）切换分支

```shell
$ git checkout -b <your-branch>
$ gcb <your-branch>
```

作用：切换到指定分支，如果该 branch 尚不存在，则会被新建

场景：在工作中经常需要新建分支，然后切换过去，这个命令结合了两者

## 撤销改变

### git checkout

可以使用如下命令“撤销”掉指定文件的本地改动：

```shell
$ git checkout -- <filename>
```

此命令会使用 HEAD 中的最新内容替换掉你的工作目录中的文件。已添加到缓存区的改动，以及新文件，都不受影响。

## 其他

### config

将配置列出来，主要是用来看用户名和邮箱

```shell
$ git config --list
$ gcf
```

## 注脚和参考

[^1]: 别名的使用需要自己配置，或者是使用插件，具体可以看本 wiki 相关条目内容

