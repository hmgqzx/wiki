---
title: Emmet 语法简单总结
---



根据当前文件的**解析模式**来判断要使用 HTML 语法还是 CSS 语法来解析

在没有后缀的文件中，你可以按下`shift + ctrl + p`呼出面板，输入`seth`就可以设置当前文件的解析模式为 HTML 

## HTML 对应语法总结

* HTML 文档初始结构
  * 输入`!`或`html:5`
* id
  * 用 `#` 标记
* class
  * 用 `.` 标记
  * 多个 class 也是用 `.` 间隔即可

### 层次控制

* 平级元素
  * `+`
* 后代
  * `>`
* 提升层次
  * `^`
  * 当使用 `div>ul>li` 的指令之后，再继续写下去，那么后续内容都是在 li 下级的。如果我想编写一个跟 ul 平级的 span 标签，那么我需要先用 `^` 提升到上一个层次。
* 重复
  * `*`
  * `ul>li*5`
* 分组
  * `()`
  * 用括号进行分组，表示一个代码块，分组内部的嵌套和层级关系和分组外部无关
  * 分组也能使用 `*`

### 其他

* 自定义属性
  * `[]`
* 编号
  * `$`
  * `ul>li.item$*5`
* ​

### **HTML 简写规则简单总结**

　　1. E 代表HTML标签。
　　2. E#id 代表id属性。
　　3. E.class 代表class属性。
　　4. E[attr=foo] 代表某一个特定属性。
　　5. E{foo} 代表标签包含的内容是foo。
　　6. E>N 代表N是E的子元素。
　　7. E+N 代表N是E的同级元素。
　　8. E^N 代表N是E的上级元素。

### 参考

[HTML/CSS 速写神器：Emmet | bubkoo](http://bubkoo.com/2014/01/04/emmet-a-toolkit-for-improving-html-css-workflow/)



## CSS 对应语法总结

单位别名

- p 表示%
- e 表示 em
- x 表示 ex



### 快捷键

- Ctrl+,
  展开缩写
- Ctrl+M
  匹配对
- Ctrl+H
  使用缩写包括
- Shift+Ctrl+M
  合并行
- Ctrl+Shift+?
  上一个编辑点
- Ctrl+Shift+?
  下一个编辑点
- Ctrl+Shift+?
  定位匹配对



[Cheat Sheet](https://docs.emmet.io/cheat-sheet/)