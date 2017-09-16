---
title: Python 字符串的常用知识
toc: true
---

## 字符串处理

### 删除字符串中不需要的字符

`strip()` 方法能用于删除开始或结尾的字符。 `lstrip()` 和 `rstrip()` 分别从左和从右执行删除操作。 默认情况下，这些方法会去除空白字符，但是你也可以指定其他字符[^1]

需要注意的是这些 `strip`方法不会对字符串的中间的文本执行去除操作。[^1]

如果要处理中间的空格，需要使用 `replace()`方法或者是用正则表达式进行替换[^1]

### 查找是否含有某个子字符串

最快、最简洁的方法是[^5]：

```python
if text in string:  
	pass
```

### str 和 数值类型的转化

Python 中的都是在方法中传入参数，非常简单[^2]：

```python
int('123')
str(123)
```



## 注脚

[^1]: [2.11 删除字符串中不需要的字符 — python3-cookbook 2.0.0 文档](https://python3-cookbook.readthedocs.io/zh_CN/latest/c02/p11_strip_unwanted_characters.html)
[^2]: [python数据类型转换（str跟int的转换） - Hello World! - CSDN博客](http://blog.csdn.net/shanliangliuxing/article/details/7920400)
[^5]: [python - What's a faster operation, re.match/search or str.find? - Stack Overflow](https://stackoverflow.com/questions/4901523/whats-a-faster-operation-re-match-search-or-str-find)

