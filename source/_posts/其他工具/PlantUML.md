---
title: PlantUML —— UML 绘图工具
---

PlantUML 是一个画图脚本语言，用它可以方便地画出许多UML图

## 官方文档

[PlantUML 语言参考文档](http://translate.plantuml.com/zh/PlantUML_Language_Reference_Guide_ZH.pdf) #中文

[PlantUML Language Reference Guide](http://plantuml.com/PlantUML_Language_Reference_Guide.pdf) 

## 特点

### 支持种类

支持的UML图包括：时序图、用例图、类图、组件图、活动图。

• Sequence diagram,
• Usecase diagram,
• Class diagram,
• Activity diagram,
• Component diagram,
• State diagram,
• Object diagram.

## 安装

You can easily install GraphViz by installing brew on your Mac machine. This could fix issues if you have installed GraphViz as .dmg package.

- `brew install libtool`
- `brew link libtool`
- `brew install graphviz`
- `brew link --overwrite graphviz`



### Sublime 插件

使用 sublime_diagram_plugin 插件

- 找到 Package Control:`Add Repository`
- 再输入 https://github.com/jvantuyl/sublime_diagram_plugin.git

[插件地址](https://github.com/jvantuyl/sublime_diagram_plugin)

默认绑定：Command + M：渲染

### Chrome 插件

Sublime的plantuml插件有点鸡肋。Chrome 下的插件 [PlantUML Viewer](https://chrome.google.com/webstore/detail/plantuml-viewer/legbfeljfbjgfifnkmpoajgpgejojooj?utm_source=chrome-ntp-icon) 可以自动刷新

## Advanced usage

[Advanced usage pages](http://plantuml.com/sitemap-advanced-usage)

可以用来生成数独等……

## 基本语法

- 使用 `title` 来指定标题
- 线条的形式：-> —> ..>
- 加冒号 `:` 来添加注释
- 使用 `== xxx ==` 来分隔时序图
- 使用 `actor` 来定义参与者
- 使用括号 `(xxx)` 来表示用例，用例用椭圆形表达

### 组件图

- 使用方括号 `[xxx]` 来表示组件
- 可以把几个组件合并成一个包，可以使用的关键字为 `package, node, folder, frame, cloud, database`。不同的关键字图形不一样。

## 参考

[使用 Sublime + PlantUML 高效地画图 - 简书](http://www.jianshu.com/p/e92a52770832) #这个是中文的，入门还可以