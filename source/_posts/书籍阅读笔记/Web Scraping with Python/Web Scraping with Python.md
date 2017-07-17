[GitHub - REMitchell/python-scraping: Code samples from the book Web Scraping with Python http://shop.oreilly.com/product/0636920034391.do](https://github.com/REMitchell/python-scraping)

#阅读进度

Crawling Across the Internet 一节有些问题，暂时跳过了

#笔记
```python
random.seed(datetime.datetime.now())
```

第一个 datetime 是 datetime module 
第二个 datetime 是 datetime Objects
.now() 返回 the current local date and time



# 第七章

#### Ordered Dict

```python
>>> # regular unsorted dictionary
>>> d = {'banana': 3, 'apple': 4, 'pear': 1, 'orange': 2}

>>> # dictionary sorted by key
>>> OrderedDict(sorted(d.items(), key=lambda t: t[0]))
OrderedDict([('apple', 4), ('banana', 3), ('orange', 2), ('pear', 1)])

>>> # dictionary sorted by value
>>> OrderedDict(sorted(d.items(), key=lambda t: t[1]))
OrderedDict([('pear', 1), ('orange', 2), ('banana', 3), ('apple', 4)])

>>> # dictionary sorted by length of the key string
>>> OrderedDict(sorted(d.items(), key=lambda t: len(t[0])))
OrderedDict([('pear', 1), ('apple', 4), ('orange', 2), ('banana', 3)])
```

将内置字典无序的item有序化

语法：OrderedDict(==sorted==(字典.items(),key = lambada t:==t[0]==))

（不太明白这里lambada的机制），含义就是 lambada `t` 是每个字典里的迭代item，t[0]就是key，t[1]就是value

#### Open Refine
[OpenRefine](http://openrefine.org/)
数据清洗工具，它的主要目的是帮你在使用数据之前挖掘、清洗数据。它以你的网页浏览器作为运行界面，这就意味着它看上去是在网上运行，但所有数据其实保存在你电脑里。

# 第八章

### text analysis

这东西竟和机器学习有很大关系！兴趣来了呢～

### Markov Models

很吊的模型呢

#### 性能测试

[14.13 给你的程序做性能测试 — python3-cookbook 2.0.0 文档](http://python3-cookbook.readthedocs.io/zh_CN/latest/c14/p13_profiling_and_timing_your_program.html)

### Six Degrees of Wikipedia: Conclusion

暂时不看这里了

### NLTK

本节内容跳过了，因为大概看了一下其他书和相关背景，已经了解一些了（就是代码没瞧过）

[Natural Language Toolkit — NLTK 3.0 documentation](http://www.nltk.org/)

[利用NLTK在Python下进行自然语言处理 - 白马负金羁 - 博客频道 - CSDN.NET](http://blog.csdn.net/baimafujinji/article/details/51051505)

> 《Python 自然语言处理》：虽然很老了，仍具有参考价值
>
> 使用 pip 安装

[NLTK笔记:简介与环境搭建 - Ourren](http://blog.ourren.com/2015/02/05/nltk_note_environment_install/)

> 个人认为其应用场景有如下几点：
>
> 1. 个性推荐，需要计算两类物品的相识度和相关度；
> 2. 情感分析，用户对商品的评价，网民对帖子或者文章的态度；
> 3. 关键字提取，对网络商品的标题提取并分类，自动摘要；
> 4. 其它，待补充；

[可爱的 Python: 自然语言工具包入门](https://www.ibm.com/developerworks/cn/linux/l-cpnltk/)

[NLTK Book](http://python.usyiyi.cn/documents/nltk_python/index.html#)

[探索 Python、机器学习和 NLTK 库 - 开源中国社区](https://www.oschina.net/question/129540_83921)

[【NLP】干货！Python NLTK结合stanford NLP工具包进行文本处理 - 伏草惟存 - 博客园](http://www.cnblogs.com/baiboy/p/nltk1.html)

[【资料汇编】结巴中文分词官方文档和源码分析系列文章 - 伏草惟存 - 博客园](http://www.cnblogs.com/baiboy/p/jieba1.html)

[python的nltk中文使用和学习资料汇总帮你入门提高_python_ThinkSAAS](http://www.thinksaas.cn/topics/0/503/503862.html)

# 第九章

## request

class `requests.Request(method=None, url=None, headers=None, files=None, data=None, params=None, auth=None, cookies=None, hooks=None, json=None)`
A user-created **Request** object.

Used to prepare a **PreparedRequest**, which is sent to the server.

Parameters:	

- method – HTTP method to use.

- url – URL to send.
- headers – dictionary of headers to send.
- **files** – dictionary of {filename: fileobject} files to multipart upload.
- **data** – the body to attach to the request. If a dictionary is provided, form-encoding will take place.
- json – json for the body to attach to the request (if files or data is not specified).
- **params** – dictionary of URL parameters to append to the URL.
- **auth** – Auth handler or (user, pass) tuple.
- cookies – dictionary or CookieJar of cookies to attach to this request.
- hooks – dictionary of callback hooks, for internal usage.

### `r.cookies.get_dict()`

**get_dict**(*domain=None*, *path=None*)

Takes as an argument an optional domain and path and returns a plain old Python dict of name-value pairs of **cookies** that meet the requirements.



### *class *requests.**Response**¶

The **Response** object, which contains a server’s response to an HTTP request.

常见的：

代码中常用 `r` 来指代 response

* response.text
  * Content of the response, in unicode.
* response.cookies
  * A CookieJar of Cookies the server sent back.
  * cookies 之下还有很多方法

### *class *requests.**Session**¶

A Requests session.

Provides cookie persistence, connection-pooling, and configuration.

### requests.auth

*class *requests.auth.**AuthBase**¶

Base class that all auth implementations derive from

*class *requests.auth.**HTTPBasicAuth**(*username*, *password*)¶

Attaches HTTP Basic Authentication to the given Request object.

# 第十章

## js

> Passing around func‐ tions as variables is also extremely useful when it comes to handling user actions and callbacks

### 库

#### jQuery

这个东西让网页爬取更难，因为是动态生成，还带动画、交互等东西，更可怕是这个东西很流行

#### google analytics

追踪用户浏览的工具

爬取网站时要丢掉追踪用的cookies，防止被发现正在爬取网站

#### google maps

使用marker插入地图

```javascript
var marker = new google.maps.Marker({
  position : new google.maps.LatLng(-23.342312,123.233423),
  map : map,
  title : 'Some marker text'
})
```

LatLng：latitude、longitude 纬度、经度

用 python 可以提取这些坐标对出来再处理

## Ajax

不用刷新页面

Asynchronous JavaScript and XML：异步

## 动态 HTML

dynamics html

该死的东西，浏览器里看到的内容是源代码生成的

### 解决方法

只有两种：

* 从 JS 里解析规则后爬取
* 模拟浏览器执行 JS 后再爬（这种应该效率很低吧）

# Selenium

[selenium 3.0.2 : Python Package Index](https://pypi.python.org/pypi/selenium)

[Python爬虫利器五之Selenium的用法 | 静觅](http://cuiqingcai.com/2599.html)

##### PhantomJS

用 PhantomJS 作为后台浏览器模拟（省去图形化界面）

[Python爬虫利器四之PhantomJS的用法 | 静觅](http://cuiqingcai.com/2577.html)

或者通过Homebrew安装。。。早知道

```
brew update && brew install phantomjs
```

##### 使用

安装：（那篇帖子里少了U）

```
pip install -U selenium
```

下载对应的 webdriver

下载驱动，然后将驱动文件路径配置在环境变量即可。

[Getting started - ChromeDriver - WebDriver for Chrome](https://sites.google.com/a/chromium.org/chromedriver/getting-started)

[Mac osx 10.11 正式版下面 /usr/bin 无法修改 - V2EX](https://www.v2ex.com/t/225975)

> 用 /user/local/bin 吧

 brew install chromedriver 即可

真是久的教程啊，还是 brew 管用～以后装东西前都要看看有没有pip、brew

### selector

`find_element_by_id`、`find_elements_by_id`

### 基本使用

```python
from selenium import webdriver
import time

driver = webdriver.PhantomJS(executable_path='phantomjs')
print(type(driver))
driver.get('http://pythonscraping.com/pages/javascript/ajaxDemo.html')  # 这里 get 到的东西就放进 driver 这个对象里的某一属性了

time.sleep(3)      # 使用time.sleep()是最糟糕的，因为它将条件设置为等待一个确切的时间段。

print(driver.find_element_by_id("content").text)

driver.close()  # 关闭浏览器的这个标签
```
#### locator

和 selector 不同

`By` object

### Xpath

基本语法

## 客户端重定向



# 图像处理



# 文字辨认

OCR

optical character recognition

pillow

## tesseract

命令行工具，不是用 `import` 导入的

run with the `tesseract` command

默认数据位置：`/usr/local/share/`



图片里明暗不一会影响识别，所以要用 Pillow 处理

## Numpy

利用科学计算来帮助 tesseract 训练出更好的 OCR 能力



