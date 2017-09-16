---
title: Hexo 博客搭建过程注意点
toc: true
---

主要记录 Hexo 搭建过程中的一些注意点和一些问题的解决方向。其他详细的基础设置等网上有大量文章，官方文档也有清晰说明

## 搭建教程

搭建教程在网上有很多（不过有些实在太冗长，按需选择），下面是推荐的几个：

* [手把手教你使用Hexo + Github Pages搭建个人独立博客 | 令狐葱@前端笔记](https://linghucong.js.org/2016/04/15/2016-04-15-hexo-github-pages-blog/) # 很好的文章

* [limedroid/HexoLearning: Hexo博客搭建全攻略](https://github.com/limedroid/HexoLearning)

## Hexo  相关

### 配置文件 _config.yml

在 Hexo 中，以 `_config.yml` 作为配置文件。

* 在站点根目录下有一份，通常称为 **站点配置文件**
* 在每个主题的目录下也有一份，称为 **主题配置文件**，用于配置主题自带的选项

新手配置时不要弄混了哦 😯 ~

**注意事项‼️**：`_config.yml` 使用的是 yaml 语言，不能有多余的空格，在每个配置选项的冒号后有且只能有一个空格

如：

```yaml
theme: next
```

### **常用**命令行

#### 本地运行，预览效果

启动 sever，在浏览器进行访问：

```shell
$ hexo s -g --debug
```

支持热更新，修改配置文件后刷新一下可以看到即时效果

但如果修改了 post，则需要重新运行一下。（命令中 g 是 generate 的缩写，s 是 sever 的缩写）

### 其他通用设置

#### read more 阅读全文

推荐使用这种方法：在 MarkDown 文章中使用 `<!-- more -->` 手动进行截断。由 Hexo 原生提供，可以精确控制需要显示的摘录内容，也可以让 Hexo 中的插件更好的识别。[^1]

## 发布到 GitHub

### 使用 git 部署[^3]

```shell
$ npm install hexo-deployer-git --save
```

 在站点配置文件添加设置：

```yaml
deploy:
  type: git
  repo: <repository url>
  branch: [branch]
  message: [message]
  
# 实例
deploy:
  type: git
  repo: git@github.com:hmgqzx/dotors.git
  branch: gh-pages
  message: "Site updated: {{ now('YYYY-MM-DD HH:mm:ss') }})"
```

部署命令：

```shell
$ hexo deploy --generate
```

### 额外再搭建另一个博客 - 项目 gh-pages 方式

GitHub上建立的每个项目(`repository`)都是可以拥有独立主页的，将 hexo 生成的静态内容放置在 gh-pages 分支下即可

当我们想额外搭建另一个博客（使用不用的主题），就可以利用这种方式，在 Github 给的域名（`http(s)://<username>.github.io`）下创建二级域名

#### Github 设置

详细步骤参考链接[^2]

``` 
~/my-personal-projects/github-repo/motors not empty, please run hexo init on an empty folder and then copy your files into it
```

因为我们是先在 Github 创建仓库，再 clone 下来，这样文件夹就非空了。需要在另一个地方 `hexo init` 一个站点，再复制过来（ master 分支）

#### hexo 设置

在 Github 设置好后，项目访问链接是这样的：

```html
http(s)://<username>.github.io/<projectname>
```

那么在 hexo 的站点配置文件中，需要这样设置，才能生成对应的链接：

```yaml
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http(s)://<username>.github.io/<projectname>
root: /<projectname>/

# 实例对照
url: https://hmgqzx.github.io/dotors/
root: /dotors/
```

原因：正如注释所说，因为项目主页站点内容是放在二级域名下的，所以要那样设置

## 注脚

[^1]: [常见问题 - NexT 使用文档](http://theme-next.iissnan.com/faqs.html)
[^2]: [手动给你的GitHub项目设置一个主页 | 把生命浪费在美好的代码上](http://coderunthings.com/2015/10/23/%E6%89%8B%E5%8A%A8%E7%BB%99%E4%BD%A0%E7%9A%84GitHub%E9%A1%B9%E7%9B%AE%E8%AE%BE%E7%BD%AE%E4%B8%80%E4%B8%AA%E4%B8%BB%E9%A1%B5/)
[^3]: [Deployment | Hexo](https://hexo.io/docs/deployment.html)

