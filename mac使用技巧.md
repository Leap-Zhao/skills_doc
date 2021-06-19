# mac使用技巧

## 1 截图相关

mac os默认截图快捷键:

- command（⌘）+ shift + 3：全屏截图

- command（⌘）+ shift + 4：局部截图

- command（⌘）+ shift + 5：窗口截图（不易解释，自己按，试一试就知道了）

mac os默认截图文件会放在桌面,下面是更改截图位置的命令行: 

```bash

# 创建截图位置
mkdir ~/Desktop/截图图库
# 更改默认截图放置的位置
defaults write com.apple.screencapture location ~/Desktop/截图图库 
```

参考: [如何修改Mac系统的默认截图保存路径]( https://jingyan.baidu.com/article/b2c186c826666ec46ef6ff32.html)



