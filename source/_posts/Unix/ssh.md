# SSH

全称为 Secure Shell，是一项创建在应用层和传输层基础上的**安全协议**，为计算机上的Shell（壳层）提供安全的传输和使用环境。[^2]

其优点是安全可靠（目前），传输的数据可以是经过压缩的[^2]

## 基本操作

### 登录

```shell
$ ssh <user-name>@<host>
# 示例
$ ssh pipi@192.168.13.202
```

### 关闭连接

关闭与对方的连接：直接输入`exit` 即可

## 其他操作

### 修改端口

默认端口是22，使用 p 参数（port）可以修改端口

```shell
$ ssh -p <port> <user-name>@<host> 
# 示例
$ ssh -p 2222 pipi@192.168.13.202
```

### 端口转发

参考[^4]

## 原理

请参考[^2][^3]

## 常见问题

### WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!

场景：一次我将树莓派 A 的 sd 卡拆下，装到另一台树莓派 B 上后，连接树莓派 B 就出现这个警告

解决方法：

```shell
$ ssh-keygen -R "you server hostname or ip"
```

原因：

在第一次 ssh 连接远程服务器时，会生成一个认证，保存在本地这边的 known_hosts。出现这个错误时，只要重新 key generate 就好[^1]

## 更多

### 我还没仔细看的

* 一篇很详细的 tutorial [^5]

## 参考

[^1]: [SSH連現時出現「WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!」解決辦法 | 電腦故我在](https://blog.allenchou.cc/warning-remote-host-identification-has-changed/)
[^2]: [Secure Shell - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/Secure_Shell)
[^3]: [SSH原理与运用（一）：远程登录 - 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2011/12/ssh_remote_login.html)
[^4]: [SSH原理与运用（二）：远程操作与端口转发 - 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2011/12/ssh_port_forwarding.html)
[^5]: [SSH Tutorial for Linux - Support Documentation](https://support.suso.com/supki/SSH_Tutorial_for_Linux)



