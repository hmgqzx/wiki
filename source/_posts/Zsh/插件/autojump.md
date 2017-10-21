---
title: autojump 自动跳转目录
toc: true
---

`autojump` 是一个目录导航插件，让你不用 `cd` 来 `cd` 去

它记录访问过的目录，实现智能跳转。使用 `autojump` 的简写 `j ＋ 目录名` ，可随意的在目录间跳转，支持各种模糊匹配、补全。[^2]

## 安装

### OS X

推荐使用 `brew` 安装：

```
brew install autojump
```

#### 其他方法[^2] 

> 虽然下面的方法可用，但是不如 brew 安装来得方便

跟其他插件一样，首先要在 `.zshrc`[^4] 中找到 `plugins=`，加入 autojump

```shell
# 各插件名之间用英文空格隔开
plugins=(git autojump)
```

除此之外，还要继续在上述文件中添加

```shell
[[ -s $(brew --prefix)/etc/profile.d/autojump.sh ]] && . $(brew --prefix)/etc/profile.d/autojump.sh
```

最后 `source ~/.zshrc` 一下

## 使用[^1]

`j` is a convenience wrapper function around `autojump`

- Jump To A Directory That Contains `foo`:

  ```
  j foo
  ```
  > 前提是要用 `cd` 命令进入过对应文件夹一次，以让 `autojump` 记录
  >
  > tips: 对于有多个可能的补全，可以按下 `tab` 来选择，看上去就像这样：
  >
  > ```shell
  > $ j mu__{你按着 tab 来到了这里，然后下面是供补全的选择}
  > mu__1__/Users/me/tutorial-projects/NeteaseCloudMusicApi
  > mu__2__/Users/me/tutorial-projects/vue/vue-cli-multi-page
  > mu__3__/Users/me/tutorial-projects/musicbox
  > mu__4__/Users/me/temp/Cocoa-mupdf
  > mu__5__/Users/me/tutorial-projects/musicbox/NEMbox
  > mu__6__/Users/me/tutorial-projects/NeteaseCloudMusicApi
  > mu__7__/Users/me/Music/网易云音乐
  > mu__8__/Users/me/tutorial-projects/vue/vue-cli-multi-page
  > mu__9__/Users/me/tutorial-projects/musicbox
  > ```

- Jump To A Child Directory:

  ```
  jc bar
  ```

- Open File Manager To Directories (instead of jumping):

  ```
  jo music

  ```

- Opening a file manager to a child directory:

  ```
  jco images
  ```

### 进阶使用

查看这篇文章[^3]，或者查看帮助及官网[^1]

## 参考

[^1]: [wting/autojump: A cd command that learns - easily navigate directories from the command line](https://github.com/wting/autojump) #官网
[^2]: [Mac-zsh 安装和使用(原创) - 陈斌彬的技术博客](https://cnbin.github.io/blog/2015/06/01/mac-zsh-an-zhuang-he-shi-yong/)
[^3]: [自动补完不算什么，一键直达目录才是终极神器](https://linux.cn/article-3401-1.html)
[^4]: [linux - What does the 'rc' in `.bashrc`, etc. mean? - Super User](http://superuser.com/questions/173165/what-does-the-rc-in-bashrc-etc-mean) # It stands for “[run commands](http://en.wikipedia.org/wiki/Run_Commands)”.

