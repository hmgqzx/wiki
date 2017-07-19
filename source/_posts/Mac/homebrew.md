---
title: Homebrew
---

Homebrew 是 Mac OS X 上的软件包管理系统，使用它可以方便地安装、更新许多软件（“无人值守”~自动化）。称之为“ Mac 必备神器”一点也不为过。

## Homebrew

### 常用命令

常用的命令没几个：

```shell
$ brew install wget # 安装源码
$ brew info svn # 显示软件的各种信息，包括版本啊源码地址啊等等
$ brew uninstall wget # 卸载软件，很爽，一键静默卸载
$ brew search git # 模糊搜索brew 支持的软件。如果不加软件名，就会列出所有它支持的软件。多的很。
$ brew list # 列出本机通过brew安装的所有软件
$ brew update # 跟新brew软件自身
$ brew upgrade wget # 更新安装过的软件,如果不加软件名，就更新所有可以更新的软件
$ brew cleanup # 清除下载的各种缓存
```


==装任何东西前都看看能不能用 brew 啊！==（很多包/软件都支持 brew 安装）

```shell
$ brew search <软件名>
```

查看 brew 安装的某个包所在路径

```shell
$ brew ls <package-name>
```

### services utility

brew services are really useful for managing system services, type `$ brew services --help` for more info.

#### 查看所有的已启用的服务

```shell
$ brew services list
```

可以用来检查某些包~如Tomcat~的运行情况（从而判断是否已正确安装）

### Cellar 包安装路径

Homebrew 安装的包在 `/usr/local/Cellar/` 下

Homebrew keeps packages (known as **kegs**) in the **Cellar**, where you can check config and data files. It is a directory located at:

```shell
$ ls /usr/local/Cellar/
```

有时因为要指定某个包的执行程序~如Tomcat等~来启动，需要填写安装路径，可以这样查找：

```shell
$ brew ls <package-name>
```

# homebrew-dupes 

> System duplicate formulae for the Homebrew package manager  —— [homebrew-dupes](https://github.com/Homebrew/homebrew-dupes)

因为 homebrew 默认的措施是：not to offer duplicates for system tools。所以当我们需要安装像 `grep`（系统自带版本太低）等系统工具时就要用到 `homebrew-dupes` 这个 repository 以作替代

## 槽点

安装 `MySQL` 就不要用 `Homebrew` 了，多台机器上试验过，会存在问题。还是推荐用官网 dmg 安装