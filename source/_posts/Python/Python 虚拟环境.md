---
title: Pyenv —— Python版本管理工具
---

pyenv可以帮助你建立多个版本的 python 环境，它们相互隔离，不会污染到系统自带的 Python（ pip 安装的包也是在各自目录下的）

# 安装

## 安装 pyenv

[pyenv 项目主页#安装步骤](https://github.com/yyuu/pyenv#installation)

```bash
$ brew update
$ brew install pyenv
```

#### 添加环境变量

`PYENV_ROOT`指向pyenv检出的根目录，并向`$PATH`添加`$PYENV_ROOT/bin`以提供访问`pyenv`这条命令的路径(这里的shell配置文件依不同SHELL而需作修改,如bash：`~/.bash_profile`，Zsh：`~/.zshrc` ）

##### ZSH

用 brew 安装的话，配置好环境变量的了（我自己又按手动方法在 zsh 里加了环境变量）

After installation, you'll still need to add

```shell
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

to your profile (as stated in the caveats). You'll only ever have to do this once.

---

[pyenv 项目主页#安装步骤](https://github.com/yyuu/pyenv#installation)
1. **Define environment variable PYENV_ROOT** to point to the path where pyenv repo is cloned and add `$PYENV_ROOT/bin` to your `$PATH` for access to the `pyenv` command-line utility.
```bash
# 我的 zsh 将环境变量放在另一个文件（env.sh）中，在那里添加环境变量就可以了
$ echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
$ echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
```
2. **Add pyenv init to your shell** to enable shims and autocompletion. Please make sure `eval "$(pyenv init -)"`is placed toward the end of the shell configuration file since it manipulates `PATH` during the initialization.
``` bash
# 使用自动完成功能，要将配置写在 shell configuration file 末尾
$ echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```
3. **Restart your shell so the path changes take effect.** 
``` bash
$ exec $SHELL # 重启shell(因为修改了$PATH)
```

## 安装 pyenv-virtualenv 

[pyenv-virtualenv 项目主页#安装步骤](https://github.com/yyuu/pyenv-virtualenv#installation)

使用 brew 安装

```bash
$ brew install pyenv-virtualenv
```

**Add pyenv virtualenv-init to your shell** to enable auto-activation of virtualenvs. This is entirely optional but pretty useful. See "Activate virtualenv" below.

```bash
# 使用自动完成等功能，直接将下面这句写在 shell configuration file (~/.zshrc) 末尾就可以
eval "$(pyenv virtualenv-init -)"

# 用命令的话是下面那样：
$ echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```

# 使用

## pyenv 使用

[命令参考 · yyuu/pyenv](https://github.com/yyuu/pyenv/blob/master/COMMANDS.md#command-reference)

`pyenv install `安装指定的版本

```bash
$ pyenv install -v 2.7.13 #添加-v参数用于显示细节
$ pyenv rehash  #安装新版本的python或者其他二进制包后都需要运行，或者重启shell
```

## pyenv-virtualenv 使用

#### 创建

创建虚拟环境--`pyenv virtualenv 版本号 虚拟环境名`。

```shell
$ pyenv virtualenv 3.5.1 venv-3.5.1
```

#### 删除

``` bash
$ pyenv uninstall my-virtual-env
# 删除时会弹出对话框，输入‘y’确认
# 或者你可以直接删除 ~/.pyenv/versions中的相应目录
```
#### 仅查看python的虚拟环境

```bash
$ pyenv virtualenvs
```

#### 自动激活

```bash
$ mkdir myproject
$ cd myproject
$ pyenv local myenv
```

#### 手动激活

You can also activate and deactivate a pyenv virtualenv manually:

```
pyenv activate <name>
pyenv deactivate
```

# 管理版本的其他简单方法

* 不要更改系统默认的python2（因为改了可能会导致系统某些用python2写的系统文件出错），每次执行时加版本号，`python` 就是2的版本，`python3`就是3的版本；用 `pip`会安装包到 2 的版本，用`pip3`会安装到 3的版本。
* 直接在自己写的程序里指定环境变量，如 `#!/usr/bin/env python3`。

# 参考

[python虚拟开发环境配置 - 简书](http://www.jianshu.com/p/9ebce087da1f) #配置好了 #相关使用可以再参考这个

[Python多版本管理器pyenv和虚拟环境pyenv-virtualenv的安装设置 - 简书](http://www.jianshu.com/p/1842a363257c)

[使用pyenv搭建python虚拟环境 - 运维之美 | 十条](http://www.10tiao.com/html/357/201604/2247483759/1.html)