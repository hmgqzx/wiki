---
title: Aria 2 —— Mac 的下载利器
toc:  true
tags: [工具推荐]
---

**Aria 2** 是一个下载利器，可以说是 Mac 和 Linux 下的 IDM（只能用于 Windows 平台）。

## 下载速度体验

刚开始使用 Mac 时，为下载问题可愁了头，Chrome、Safari 等浏览器很多时候速度很慢。Mac 版百度云网盘更是没眼看。

使用 Aria 2 下载百度云网盘资源，一般可达到满速的 30%，不掉速，还算可以接受（除此之外我也不知道其他更好的办法了 😅）

下载一般 http 协议资源，基本满速

## 安装和配置

用 `brew` 安装；没什么特殊需求的话，基本开箱即用

自定义配置可参考这里[^config]

## 常用命令

### 下载多个文件

**从文件读取**

文件中的链接一行一个即可；默认同时最多下载 5 个（即`-j5`）

``` shell
$aria2c -i /Users/me/Downloads/aria2c-url.txt
```

因为 Aria2c 只支持一个实例，所以同时下载多个文件时要用这种方法，建一个 alias 非常方便

## 参考

[^config]: [Aria 2——下载器中的小清新 | SinoSky](https://www.sinosky.org/aria2-minimalist-dl-mgr.html)

[Aria2c 使用举例](http://sydi.org/posts/linux/aria2c-usage-sample-cns.html) #虽是中文，但很多过时了，不如看 官方 help

