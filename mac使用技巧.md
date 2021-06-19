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

## 2 文件已损坏

解决问题办法：

- 办法1: 系统偏好设置 -> 安全性与隐私 -> 通用 -> 选择“任何来源”
  ```bash
  #显示"任何来源"选项在控制台中执行：
  sudo spctl --master-disable
  #不显示"任何来源"选项在控制台中执行：
  sudo spctl --master-enable
  ```
  
- 办法2: 如果选择了任何来源还是提示文件已损坏，命令行输入
  ```bash
  sudo xattr -r -d com.apple.quarantine 
  # 例如：如果不知道具体路径，可以打开应用程序窗口，然后拖拽软件的图片到命令行 就可以了
  sudo xattr -r -d com.apple.quarantine  /Applications/WebStorm.app
  ```
  

