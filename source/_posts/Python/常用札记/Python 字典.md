---
title: Python 字典的常用知识
toc: true
---

## 字典处理

#### 合并两个字典

如果使用 Python 3.5+，那么如下方式是最快、最简洁、最 Pythonic 的[^3][^4]：

```python
combine-dict = {**dictA, **dictB}
```

这段代码在功能上与如下方案是等价的：
新建了一个空字典，然后依次往里面填充了来自`dictA`和`dictB`的元素

```python
combine-dict = {}
combine-dict.update(dictA)
combine-dict.update(dictB)
```

## 注脚

[^3]: [The Idiomatic Way to Merge Dictionaries in Python - Trey Hunner](https://treyhunner.com/2016/02/how-to-merge-dictionaries-in-python/)
[^4]: [怎样合并字典最符合Python语言习惯？| 编程派 | Coding Python](http://codingpy.com/article/the-idiomatic-way-to-merge-dicts-in-python/)