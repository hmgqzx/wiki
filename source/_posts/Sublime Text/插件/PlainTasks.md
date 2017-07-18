---
title: PlainTasks
toc:  true
tags: [番茄工作法]
---
PlainTasks 是一个Sublime Text 插件，可以用来管理 todo-list。

我目前是利用它来帮助践行番茄工作法（每天的 todo 作为单独的一个文件记录，如`2017-07-16.todo`；脑里蹦出来的注意放在临时的`collect.todo`；经过整理、安排后的将来计划放入`activity-inventory.todo`）

阅读插件主页获取更多信息：[aziz/PlainTasks: An opinionated todo-list plugin for Sublime Text editor (version 2 and 3)](https://github.com/aziz/PlainTasks)

## 笔记

下面是我学习使用该插件过程中的一点笔记（较简略，我只是为了掌握更多所需的内容而摘抄节选在此）

* 标签快捷添加
  * type `t`, press `tab` — it’ll become `@today` — this one is highlighted differently than other tags;
  * `c`, `tab` — `@critical`;
  * `h`, `tab` — `@high`;
  * `l`, `tab` — `@low`;



* 打开超链接：`cmd + shift + U`
  * 超链接格式：<skype:nickname>


* file link：.\filename ，一行一个文件
  * 有点疑惑，支持什么格式?——在 tutorial 里有，在 preferences->package setting 中
* notes
  * Use `_` or `*` for italic and bold just like in Markdown.



* 截止日期 （`高频使用`）
  * `d`, tab — `@due( )`
  * 详细格式见下面

### Editor Useful Tools:

* Use `⌘ + control + up/down` to move tasks up and down.
* Use `⌘ + r` to see a list of projects and quickly jump between them

### due 格式

比较常用的：

| Notation      | Meaning                                  |
| ------------- | ---------------------------------------- |
| `@due(+)`     | tomorrow as well as `@due( +1)` or `@due( +1d)` |
| `@due(+2:)`   | two hours since current date             |
| `@due(+:555)` | 555 minutes since current date           |

解释：格式是 `+[number][DdWw][h:m]`

`[ ]`里的选项是可选的，当没有指定`[DdWw]`的选项时，`[number]`默认是天数，单独指定小时使用`[h:]`，单独指定分钟数使用`[:m]`（因为要指定是0 hour，不然少了 `:` 就解析为天数了）

更多请看插件主页

### Changing color scheme

我不喜欢默认的屎黄色……还是黑色好点。在 `preferences->package setting` 中可以找到设置，里面的配置文件提供了几个主题

>If you don't like colors used in bundled schemes just copy any `.hidden-tmTheme` from PlainTasks to your User directory, change colors and paste the code below in your user settings file:
>```
>{ "color_scheme": "Path to your custom color scheme file. e.g. Packages/User/custom_plaintasks.hidden-tmTheme" }
>```
>**N.B.**, sometimes you have to restart Sublime Text to apply changes made in tmTheme file.
>**N.B.**, `scope_past_due`, `scope_due_soon`, and `scope_misformatted` settings can assign any scopes defined in tmTheme file, e.g. you can set `"scope_past_due": "my.own.super.expired.whatever"` and then just add style definition in tmTheme for this scope.

## 其他

### 预览（Mac 空格键）

[qlstephen](https://github.com/whomwah/qlstephen) 这个插件虽然声称只是用来预览 without a file extension 的纯文本，但经测试，也可以预览 .todo 后缀的文件