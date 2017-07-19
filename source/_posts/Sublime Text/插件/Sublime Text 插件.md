---
title: Sublime Text 插件
---

# 参考

> 写这篇之前已经安装几个不错的插件，因为熟悉了所以没有记录在这里——包括 package control的配置等；建议参考如下链接

[sublime text3 常用插件 · GitBook](https://www.gitbook.com/book/gongwenyi/sublime-text3-plugins/details)

[如何优雅地使用Sublime Text | 晚晴幽草轩](http://www.jeffjade.com/2015/12/15/2015-04-17-toss-sublime-text/#two)

[一个前端程序猿的Sublime Text3的自我修养 | 三省吾身丶丶](https://blog.guowenfh.com/2015/12/26/SublimeText/)

[jikeytang/sublime-text: sublime-text](https://github.com/jikeytang/sublime-text#plugins)



# 我近期尝试中的其他插件

### AdvancedNewFile 快速新建文件

- 假设有文件夹`file`。我们正在输入代码，又想在新的子目录下新建html文件的话用传统方式得很多步，新建目录，新建文件，保存等等等。
- 但是有了该插件之后，事情就变得简单了许多，只需要按下`Ctrl+Shift+N`，输入文件夹以及文件名，你就会看到如下效果:（回车，你会发现已经子目录下的文件已经新建完成了！）


> 还没配置好,不太会用

### HTML-CSS-JS Prettify 代码格式化
其实有了这个代码格式化插件，就可以删除上面的代码格式化插件了。因为功能确实强大！

- [官网插件配置](https://packagecontrol.io/packages/HTML-CSS-JS%20Prettify)
- [FED社区：sublime text 3 插件：HTML-CSS-JS Prettify](http://frontenddev.org/article/sublime-does-text-three-plug-ins-html-and-css-js-prettify.html)

其实我把官网的配置趴下来之后就改了两个地方：

- `"selector_separator_newline": false`： 不需要每个CSS选择器单独占一行
- `"allowed_file_extensions": ["..这是老的，新增在-->","vue"],`：将`vue`的组件当成`html`来进行格式化
- 默认快捷键：`cmd+Shift+H`



###liveReload 文件保存浏览器即时刷新
> 该插件在window下，有很多问题会导致不能使用，mac下可以正常使用

- 需安装对应的chrome插件：[chrome商店下载](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei)，完成后需勾选允许访问文件网址
- 为了避免每一次启动实时刷新在sulime里面启动一遍插件，可在插件设置中增加如下字段：

```
{
    "enabled_plugins": [
        "SimpleReloadPlugin",
        "SimpleRefresh"
    ]
}
```

这时就只需要在浏览器端点一下小圆圈就好了

### FileDiffs 比较文件差异

> 手下的几个码农的代码风格与自己并不相同，经常代码汇总过来我都不知道他们改了什么，这个插件还是很给力的。

