---
title: pyc文件
---

[Python什么情况下会生成pyc文件？ - 知乎](https://www.zhihu.com/question/30296617)

简单来说，".pyc" 就是编译过的 ".py" 源代码

## 具体过程

如果 Python 进程在机器上拥有写入权限，那么它将把程序的字节码保存为一个以 .pyc 为扩展名的文件。当程序运行之后，你会在那些源代码的附近（也就是说同一个目录下）看到这些文件

## 作用

Python这样保存字节码是作为一种启动速度的优化。下一次运行程序时，如果你在上次保存字节码之后没有修改过源代码的话，Python将会加载.pyc文件并`跳过编译`这个步骤。当Python必须重编译时，它会自动检查源文件和字节码文件的时间戳：如果你又保存了源代码，下次程序运行时，字节码将自动重新创建。



A program `doesn't run any faster` when it is read from a ‘.pyc’ or ‘.pyo’ file than when it is read from a ‘.py’ file; the only thing that's faster about ‘.pyc’ or ‘.pyo’files is the speed with which they are `loaded`.

.pyc 文件的作用是提高 load 的速度



When a script is run by giving its name on the command line, the bytecode for the script is never written to a ‘.pyc’ or ‘.pyo’ file. Thus, the startup time of a script may be reduced by moving most of its code to a module and having a small bootstrap script that imports that module. It is also possible to name a ‘.pyc’ or ‘.pyo’file directly on the command line.

在 import 别的 py 文件时，那个 py 文件会被存一份 pyc 加速下次装载。而主文件因为只需要装载一次就没有存 pyc。