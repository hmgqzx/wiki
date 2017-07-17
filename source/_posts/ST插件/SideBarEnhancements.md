`SideBarEnhancements`是一个快捷键增强插件，使用最广泛的就是用来定义浏览器预览文件。

打开`Package Setting > Side Bar > Key Bindings - User`即可自定义浏览器预览快捷键，如下代码定义`chrome`所示：

```json
[
    //borwser preview.
    {
        "keys": ["f2"],
        "command": "side_bar_files_open_with",
        "args": {
            "paths": [],
            "application": "/Applications/Google Chrome.app",
            "extensions": ".*"
        }
    }
]
```

`keys`字段表示绑定的快捷键，`command`字段表示关联的程序，`application`表示要打开的软件，最后`extensions`表示将要使用软件打开何种扩展文件，`.*`表示所有文件。