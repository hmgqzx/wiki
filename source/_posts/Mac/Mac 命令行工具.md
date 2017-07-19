---
title: Mac OS X 里特有的那些命令行
toc:  true
tags: [配置,小技巧]
---
Mac 里的不少配置可以通过特定的命令行来设定，以下是我比较常用的、感兴趣的命令。我一般是在 zsh 里对这些常用的命令设定 alias，非常方便。
*更多的命令请参考：*

* [herrbischoff/awesome-osx-command-line: Use your OS X terminal shell to do awesome things.](https://github.com/herrbischoff/awesome-osx-command-line) 


### Finder

#### Show All File Extensions 显示所有的文件扩展名

```
defaults write -g AppleShowAllExtensions -bool true
```

#### Hide Folder in Finder 隐藏 Finder 里的指定文件夹

```
chflags hidden /path/to/folder/
```

#### Show Hidden Files 显示隐藏文件

隐藏文件是指以`.`开头的系统文件等，在 Finder 里默认隐藏；开启显示后，数目会很多，建议平时不用时关闭

```
# Show All #要重启才行？
defaults write com.apple.finder AppleShowAllFiles true

# Restore Default File Visibility
defaults write com.apple.finder AppleShowAllFiles false
```

#### Unhide User Library Folder 不隐藏用户的库文件夹

```
chflags nohidden ~/Library
```

#### Increase Number of Recent Places 增加 Finder 中的“最近使用文件夹”数量

```
defaults write -g NSNavRecentPlacesLimit -int 10 && \
killall Finder
```

#### Show "Quit Finder" Menu Item 设定 Finder 可退出（`强烈推荐`）

> Makes possible to see Finder menu item "Quit Finder" with default shortcut Cmd + Q

这个好用，这样就能使用 `Cmd + Q` 一次性关闭所有的 Finder 窗口了

```
# Enable
defaults write com.apple.finder QuitMenuItem -bool true && \
killall Finder

# Disable (Default)
defaults write com.apple.finder QuitMenuItem -bool false && \
killall Finder
```

#### Path Bar	显示路径栏

开启后会在 Finder  底部显示当前路径信息

```
# Show
defaults write com.apple.finder ShowPathbar -bool true

# Hide (Default)
defaults write com.apple.finder ShowPathbar -bool false
```

#### Status Bar 状态栏

在 Finder 最底部，显示当前文件夹项目数量、光标选中数量、硬盘可用容量

```
# Show
defaults write com.apple.finder ShowStatusBar -bool true

# Hide (Default)
defaults write com.apple.finder ShowStatusBar -bool false
```

#### Set Current Folder as Default Search Scope 设置当前文件夹为默认搜索域

整理有序的话，大部分情况下只是搜索当前目录，这样就不用每次都要多点击一次来选择了

```
defaults write com.apple.finder FXDefaultSearchScope -string "SCcf"
```

### Layout

#### Desktop Icon Visibility 显示/隐藏桌面图标

OS X 桌面的右键功能里没有 Windows 的“隐藏桌面图标”选项，可以通过下面的命令实现

```
# Hide Icons
defaults write com.apple.finder CreateDesktop -bool false && \
killall Finder

# Show Icons (Default)
defaults write com.apple.finder CreateDesktop -bool true && \
killall Finder
```

### Battery 电池

哈哈，这个纯粹是列在这儿，平时并没多大用

#### Remaining Battery Percentage 剩余电量

```shell
pmset -g batt | egrep "([0-9]+\%).*" -o --colour=auto | cut -f1 -d';'
```

#### Remaining Battery Time 电池剩余使用时间

```shell
pmset -g batt | egrep "([0-9]+\%).*" -o --colour=auto | cut -f3 -d';'
```

### Power Management 电源管理

#### Prevent System Sleep 防止系统进入睡眠一段时间

参数单位是秒

Prevent sleep for 1 hour:

```
caffeinate -u -t 3600
```

#### Put Display to Sleep after 15 Minutes of Inactivity 一段时间不活动后关闭显示器

参数单位是分钟

```
sudo pmset displaysleep 15
```

#### Put Computer to Sleep after 30 Minutes of Inactivity 一段时间不活动后使 Mac 睡眠

参数单位是分钟

```
sudo pmset sleep 30
```

#### Check System Sleep Idle Time 查看系统进入休眠的间隔

目前我的是 1 分钟

```shell
$ sudo systemsetup -getcomputersleep
Computer Sleep: after 1 minutes
```

#### Set System Sleep Idle Time to 60 Minutes 设置系统进入休眠的间隔

```
sudo systemsetup -setcomputersleep 60
```

### Audio

#### Set Audio Volume

```
osascript -e 'set volume 4'
```

#### Play Audio File

You can play all audio formats that are natively supported by QuickTime.

```
afplay -q 1 filename.mp3
```

### TTS

吐槽下，综合各方面考虑，Mac 上可用的 TTS 大概最好的就是系统自带的了。然而——还是那么地垃圾…… 

#### Speak Text with System Default Voice 用 TTS 发音朗读文本

```
say 'All your base are belong to us!'
```

#### Create Audiobook From Text

Uses "Alex" voice, a plain UTF-8 encoded text file for input and AAC output.

```
say -v Alex -f file.txt -o "output.m4a"
```

### Networking Tools 网络工具

#### Ping a Host to See Whether It’s Available 

这个大概是天朝特色了……

```
ping -o github.com
```

#### Troubleshoot Routing Problems

```
traceroute github.com
```

### SSH

#### Remote Login 远程登录

```
# Enable remote login
sudo launchctl load -w /System/Library/LaunchDaemons/ssh.plist

# Disable remote login
sudo launchctl unload -w /System/Library/LaunchDaemons/ssh.plist
```

### TCP/IP

#### Show Application Using a Certain Port 显示当前占用特定端口的应用列表 （`强烈推荐`）

这个用来检查端口占用很不错

This outputs all applications currently using port 80.

```
sudo lsof -i :80
```

#### Show External IP Address

```
dig +short myip.opendns.com @resolver1.opendns.com
```

### Wi-Fi

#### Show Local IP Address

```
ipconfig getifaddr en0
```

#### Show Wi-Fi Connection History

```
defaults read /Library/Preferences/SystemConfiguration/com.apple.airport.preferences | grep LastConnected -A 7
```

#### Show Wi-Fi Network Passwords

Exchange SSID with the SSID of the access point you wish to query the password from.

```
security find-generic-password -D "AirPort network password" -a "SSID" -gw
```

### Spotlight

这个要怎么用？听说这个很久了，还没去具体了解使用

#### Spotlight Indexing

```
# Disable
mdutil -i off -d /path/to/volume

# Enable (Default)
mdutil -i on /path/to/volume
```

#### Erase Spotlight Index and Rebuild 重建索引

```
mdutil -E /path/to/volume
```

#### Search via Spotlight 搜索

```
mdfind -name 'searchterm'
```

#### Show Spotlight Indexed Metadata

```
mdls /path/to/file
```

### Screenshots 屏幕截图

目前在用软件`Snip`，满足基本所需了

#### Take Delayed Screenshot

Takes a screenshot as JPEG after 3 seconds and displays in Preview.

```
screencapture -T 3 -t jpg -P delayedpic.jpg
```

#### Save Screenshots to Given Location

Sets location to `~/Desktop`.

```
defaults write com.apple.screencapture location ~/Desktop && \
killall SystemUIServer
```

#### Save Screenshots in Given Format

Sets format to `png`. Other options are `bmp`, `gif`, `jpg`, `jpeg`, `pdf`, `tiff`.

```
defaults write com.apple.screencapture type -string "png"
```

#### Disable Shadow in Screenshots 隐藏截图里的阴影

有阴影好看很多

```
defaults write com.apple.screencapture disable-shadow -bool true && \
killall SystemUIServer
```

#### Set Default Screenshot Name

Date and time remain unchanged.

```
defaults write com.apple.screencapture name "Example name" && \
killall SystemUIServer
```

### Login Window

#### Set Login Window Text

```
sudo defaults write /Library/Preferences/com.apple.loginwindow LoginwindowText "Your text"
```

### Security

### Application Firewall

这个是不是可以阻止应用联网？？（之前试了下，好像没什么效果，😓）

#### Firewall Service

```
# Show Status
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --getglobalstate

# Enable
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --setglobalstate on

# Disable (Default)
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --setglobalstate off
```

#### Add Application to Firewall

```
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --add /path/to/file
```

### Passwords

#### Generate Secure Password and Copy to Clipboard

```
LC_ALL=C tr -dc "[:alpha:][:alnum:]" < /dev/urandom | head -c 20 | pbcopy
```

### Physical Access

#### Launch Screen Saver  启动屏幕保护程序

```
open /System/Library/Frameworks/ScreenSaver.framework/Versions/A/Resources/ScreenSaverEngine.app
```

#### Lock Screen 锁屏

```
/System/Library/CoreServices/Menu\ Extras/User.menu/Contents/Resources/CGSession -suspend
```

#### Screensaver Immediate Lock

```
# Status
defaults read com.apple.screensaver askForPasswordDelay

# Enable (Default)
defaults write com.apple.screensaver askForPasswordDelay -int 0

# Disable (Integer = lock delay in seconds)
defaults write com.apple.screensaver askForPasswordDelay -int 10
```

#### Screensaver Password

```
# Status
defaults read com.apple.screensaver askForPassword

# Enable
defaults write com.apple.screensaver askForPassword -int 1

# Disable (Default)
defaults write com.apple.screensaver askForPassword -int 0
```

#### Shutdown 关机

```
sudo poweroff
```

#### Uptime 已开机时间

How long since your last restart.

```shell
$ uptime
15:38  up 19 days, 14:48, 6 users, load averages: 1.85 1.55 1.47
```
