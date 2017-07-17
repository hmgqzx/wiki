aziz/PlainTasks: An opinionated todo-list plugin for Sublime Text editor (version 2 and 3)

- type t, press tab — it’ll become @today — this one is highlighted differently than other tags;
- c, tab — @critical;
- h, tab — @high;
- l, tab — @low;



* 打开超链接：cmd + shift + U
  * 超链接格式：<skype:nickname>


* file link：.\filename ，一行一个文件
  * 有点疑惑，支持什么格式——在 tutorial 里有，在 preferences->package setting 中
* notes
  * Use `_` or `*` for italic and bold just like in Markdown.



* 截止日期
  * `d`, tab — `@due( )`

### Editor Useful Tools:

☐ Use **⌘ + control + up/down**  to move tasks up and down.

☐ Use **⌘ + r** to see a list of projects and quickly jump between them



## due 格式

@due( +1d)



### Changing color scheme

If you don't like colors used in bundled schemes just copy any `.hidden-tmTheme` from PlainTasks to your User directory, change colors and paste the code below in your user settings file:

```
{ "color_scheme": "Path to your custom color scheme file. e.g. Packages/User/custom_plaintasks.hidden-tmTheme" }
```

**N.B.**, sometimes you have to restart Sublime Text to apply changes made in tmTheme file.

**N.B.**, `scope_past_due`, `scope_due_soon`, and `scope_misformatted` settings can assign any scopes defined in tmTheme file, e.g. you can set `"scope_past_due": "my.own.super.expired.whatever"` and then just add style definition in tmTheme for this scope.

> 在 preferences->package setting 中

## 预览

[qlstephen](https://github.com/whomwah/qlstephen) 这个插件虽然是用来预览 without a file extension 的纯文本，但经测试，也可以预览 .todo！