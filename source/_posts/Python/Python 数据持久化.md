---
title: Python 数据持久化
---

## 参考

[Python 数据持久化方式——JSON与Pickle - BrieflyX's Base](http://brieflyx.me/2015/python-module/python-data-persistence/)

[pickle| Hmgqzx's Wiki](https://hmgqzx.github.io/wiki/Python/pickle)

## JSON 和 Pickle 的比较

- JSON是文本形式的存储，Pickle则是二进制形式（至少常用二进制）
- JSON是人可读的，Pickle不可读
- JSON广泛应用于除Python外的其他领域，Pickle是Python独有的。
- JSON只能dump一些python的内置对象，**Pickle可以存储几乎所有对象**。

