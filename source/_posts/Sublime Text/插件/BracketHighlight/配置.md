---
title: BracketHighlight 配置
---

## 参考

[Customizing - BracketHighlighter Documentation](https://facelessuser.github.io/BracketHighlighter/customize/#configuring-highlight-style)

[//Sublime Text Love - Plugin: BracketHighlighter - 括號高亮](http://sublimetextlove.tumblr.com/post/42363199041/brackethighlighter)

[SublimeText插件BracketHighlighter配置 |](http://www.darkpool.net/archives/95)

## 我的笔记

### 高亮方式

支持4种高亮方式:`underline/outline/highlight/solid`

==不用重启就能看到修改效果==

### 括号种类

| name              | meaning          |
| ----------------- | ---------------- |
| Bracket Tag       | `<tag> </tag>`   |
| Bracket Curly     | `{ }`            |
| Bracket Round     | `( )`            |
| Bracket Square    | `[ ]`            |
| Bracket Quote     | `' '` 、`" "`     |
| Bracket Unmatched | 没有成对匹配到的符号（所有种类） |

### 我的配置

> 以下是我自己 Mac 上的配置，路径什么的根据自己灵活变通更改就好

主要有两个地方要改：

**My personal configuration: bh_core.sublime-settings**

复制默认的值进入

`/Users/me/Library/Application\ Support/Sublime\ Text\ 3/Packages/User`

然后根据喜好更改高亮方式

**My personal configuration: [Default Theme].tmTheme**

这个配置主要是更改 foreground color（前景色），也就是高亮颜色

方法：

* 上 [TmTheme Editor](https://tmtheme-editor.herokuapp.com/#!/editor/theme/Monokai) 里搞个 tmTheme 文件下来, 放入 `/Users/me/Library/Application\ Support/Sublime\ Text\ 3/Packages/User` 中
* 打开主题文件,添加如下代码 在<array>下方，与其它<dict>标签对齐

```xml
<dict>
    <key>name</key>
    <string>Bracket Tag</string>
    <key>scope</key>
    <string>brackethighlighter.tag</string>
    <key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#66CCCC</string>
    </dict>
</dict>
<dict>
    <key>name</key>
    <string>Bracket Curly</string>
    <key>scope</key>
    <string>brackethighlighter.curly</string>
    <key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#CC99CC</string>
    </dict>
</dict>
<dict>
    <key>name</key>
    <string>Bracket Round</string>
    <key>scope</key>
    <string>brackethighlighter.round</string>
    <key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#FFCC66</string>
    </dict>
</dict>
<dict>
    <key>name</key>
    <string>Bracket Square</string>
    <key>scope</key>
    <string>brackethighlighter.square</string>
    <key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#6699CC</string>
    </dict>
</dict>
<dict>
    <key>name</key>
    <string>Bracket Angle</string>
    <key>scope</key>
    <string>brackethighlighter.angle</string>
    <key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#F99157</string>
    </dict>
</dict>
<dict>
    <key>name</key>
    <string>Bracket Quote</string>
    <key>scope</key>
    <string>brackethighlighter.quote</string>
    <key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#99CC99</string>
    </dict>
</dict>
<dict>
    <key>name</key>
    <string>Bracket Unmatched</string>
    <key>scope</key>
    <string>brackethighlighter.unmatched</string>
    <key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#F2777A</string>
    </dict>
</dict>
```

