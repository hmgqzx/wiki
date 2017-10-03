---
title: Dock
toc: true
---

## 综合设置

### 只显示已打开应用[^1]

```shell
defaults write com.apple.dock static-only -boolean true; killall Dock
# 恢复为默认设置：
defaults delete com.apple.dock static-only; killall Dock
```

### 关掉 Dock 动画

主要参考：[^2]

## 隐藏 dock 特定 app 图标

### 主要原理

在 Info.plist  添加

```xml
<key>LSUIElement</key>
<true/>
```

LSUIElement 是 Launch Services Keys [^9]中的一项。其 Specifies whether the app is an agent app, that is, an app that should not appear in the Dock or Force Quit window. [^10]

If this key is set to `YES`, Launch Services runs the app as an agent app. [^10]

### cli

可以用如下命令[^8]：

```shell
defaults write /Applications/Adium.app/Contents/Info.plist LSUIElement true
```

### 乱码问题

用其他编辑器打开 `Info.plist` 时，有可能乱码（我不知道什么原因），这时可以使用 Xcode 来打开。它的 Property List Editor 也使得阅读选项非常清晰。[^11]

## 参考

[^1]: [装点你的 Dock：外观篇丨一日一技 · Mac - 少数派](https://sspai.com/post/33493)
[^2]: [Mac 加速：干掉那些「炫酷」的动画 - MacTips - 知乎专栏](https://zhuanlan.zhihu.com/p/20667030)
[^8]: [macos - Hide Adium (or any other app's) icon in the dock - Ask Different](https://apple.stackexchange.com/questions/130390/hide-adium-or-any-other-apps-icon-in-the-dock)
[^9]: [Launch Services Keys](https://developer.apple.com/library/content/documentation/General/Reference/InfoPlistKeyReference/Articles/LaunchServicesKeys.html)
[^10]: [Launch Services Keys](https://developer.apple.com/library/content/documentation/General/Reference/InfoPlistKeyReference/Articles/LaunchServicesKeys.html#//apple_ref/doc/uid/20001431-108256)
[^11]: [macos - Hide Adium (or any other app's) icon in the dock - Ask Different](https://apple.stackexchange.com/questions/130390/hide-adium-or-any-other-apps-icon-in-the-dock/131136#131136)
