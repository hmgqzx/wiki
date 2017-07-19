---
title: Python collections模块
tags: [Python模块]
---

# collections模块

## Ordered Dict

[不可不知的Python模块: collections | piglei's blog](http://www.zlovezl.cn/articles/collections-in-python/)

在Python中，dict这个数据结构由于hash的特性，是无序的

内置字典：

可以看到，在迭代时是“乱”序的

```python
a = dict(one=1, two=2, three=3, four=4)
print(a)
for k, v in a.items():
    print(k, v)

# run:
{'three': 3, 'four': 4, 'one': 1, 'two': 2}
three 3
four 4
one 1
two 2
```
OrderedDict：

```python
from collections import OrderedDict

b = OrderedDict(one=1, two=2, three=3, four=4)
print(b)
for k, v in b.items():
    print(k, v)
    
# run:
OrderedDict([('one', 1), ('two', 2), ('four', 4), ('three', 3)])
one 1
two 2
four 4
three 3
```

顺序以添加顺序为准，和修改的顺序无关。