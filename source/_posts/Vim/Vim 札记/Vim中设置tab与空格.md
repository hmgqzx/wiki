---
title: Vim 中设置 tab 自动转换为 4 个空格
toc: true
---

## 设置方法

在 `.vimrc` 文件（没有就在 `$HOME` 下新建一个）中设置[^c]：

```sh
filetype plugin indent on
" show existing tab with 4 spaces width
set tabstop=4
" when indenting with '>', use 4 spaces width
set shiftwidth=4
" Sets the number of columns for a TAB
set softtabstop=4
" On pressing tab, insert 4 spaces
set expandtab
```
另一个回答附有有更通俗的注释[^b]：
```shell
filetype plugin indent on
set tabstop=4       " The width of a TAB is set to 4.
                    " Still it is a \t. It is just that
                    " Vim will interpret it to be having
                    " a width of 4.

set shiftwidth=4    " Indents will have a width of 4

set softtabstop=4   " Sets the number of columns for a TAB

set expandtab       " Expand TABs to spaces
```

### filetype 命令说明

文档说明[^e][^f]

```shell
filetype plugin indent on
```

这行命令主要是用于开启文件类型检测

#### 作用

> vim通过对文件类型的识别，可以为不同类型的文件，设置不同的选项值、定义不同键绑定等。例如，对于c类型的文件，它就和bash脚本有不同的注释格式、不同的缩进格式、不同的关键字等。vim在设置文件类型后，会触发FileType事件，执行FileType相关的自动命令，对不同类型的文件区别对待。[^g]

## commands 命令具体说明

以下列出了设置时需要使用的命令的说明：*tabstop*, *shiftwidth*, *expandtab*, 和 *softtabstop* 

### tabstop

> Set tabstop to tell vim how many columns a tab counts for.[^a]

tabstop 设置 vim 中每个 tab 展开的列数

### softtabstop

> Set softtabstop to control how many columns vim uses when you hit Tab in insert mode.[^a]

顾名思义，`softtabstop` 是 `tabstop` 的 soft 版本

### expandtab
> When expandtab is set, hitting Tab in insert mode will produce the appropriate number of spaces.[^a]

对 expandtab 进行设置后，点击 tab 就会将其转换为对应数量的空格

### shiftwidth

> Set shiftwidth to control how many columns text is indented with the reindent operations (<< and >>) and automatic C-style indentation.[^a]

### 综合

| 设置情况                                     | Vim 行为                          |
| ---------------------------------------- | ------------------------------- |
| `softtabstop` < `tabstop`；` expandtab` 没有设置 | 混合使用 tab 和 space 来生成期望的 spacing |
| `softtabstop` = `tabstop`；` expandtab` 没有设置 | 总是使用 tab                        |
| 设置了 ` expandtab`                         | 总是使用 空格                         |

可以看到，我们应该设置 ` expandtab`，以让 Vim 自动将 tab 转换成对应的空格

## 参考

[^a]: [Secrets of tabs in vim](http://tedlogan.com/techblog3.html)
[^b]: [vim - Redefine tab as 4 spaces - Stack Overflow](https://stackoverflow.com/questions/1878974/redefine-tab-as-4-spaces/1878984#1878984)
[^c]: [whitespace - Tab key == 4 spaces and auto-indent after curly braces in Vim - Stack Overflow](https://stackoverflow.com/questions/234564/tab-key-4-spaces-and-auto-indent-after-curly-braces-in-vim)
[^d]: [vimrc - What is `softtabstop` used for? - Vi and Vim Stack Exchange](https://vi.stackexchange.com/questions/4244/what-is-softtabstop-used-for)
[^e]: [indentation - What is the difference between `filetype plugin indent on` and `filetype indent on`? - Vi and Vim Stack Exchange](https://vi.stackexchange.com/questions/10124/what-is-the-difference-between-filetype-plugin-indent-on-and-filetype-indent)
[^f]: [Vim documentation: filetype](http://vimdoc.sourceforge.net/htmldoc/filetype.html) (英）[VIM: filetype](http://vimcdoc.sourceforge.net/doc/filetype.html)（中）
[^g]: [vi/vim使用进阶: 开启文件类型检测 – 易水博客](http://easwy.com/blog/archives/advanced-vim-skills-filetype-on/)