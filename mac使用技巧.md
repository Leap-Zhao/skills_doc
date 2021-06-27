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

## 3 .bash_profile添加

如果安装了oh_my_zsh,可以添加相关配置,便于工作使用

.zshrc 添加如下内容

```shell
# add by feiyue,2018.11.25
# if you want the .bash_profile to take effect,add following sentence
source ~/.bash_profile
```
.bash_profile内容如下:

```shell
# add by feiyue 2021-06-22
# 添加python3.7相关的环境变变&对应pip3安装后的bin文件
PATH="/Users/feiyue/Library/Python/3.7/bin:$PATH"

# add by feiyue 2021-04-18
# 添加nginx相关的环境变量
export NGINX_ROOT=/usr/local/Cellar/nginx/1.15.9/
export NGINX_LOG=/usr/local/Cellar/nginx/1.15.9/logs
export NGINX_CONF=/usr/local/etc/nginx/

# add by feiyue 2020-10-23
# add mybin folder
# 添加mybin到PATH环境变量中去
PATH="/Users/feiyue/mybin:$PATH"

# add by feiyue 2020-08-13
# add multi gopath for many go project
# 添加GOPATH && GOBIN 等go相关的环境变量
export GOPATH=/Users/feiyue/MyStudy/go_study
export GOBIN=$GOPATH/bin
PATH="$GOBIN:$PATH"

# add by feiyue 2019-10-20
# add Cellar bin folder
# 添加brew安装的可执行文件路径到PATH环境变量中去
PATH="/usr/local/bin:$PATH"
# 添加homebrew的安装源
export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles

# added automatic by Miniconda2 installer
export PATH="/Users/feiyue/Applications/minicode2/bin:$PATH"

# add by feiyue 2019-0
# python virtualenv folder
export WORKON_HOME=~/env
# source /Users/feiyue/Applications/minicode2/envs/python3.6/bin/virtualenvwrapper.sh

# add by feiyue 2019-02-18
# mysql bin folder
PATH=$PATH:/usr/local/mysql/bin

#=====================================================
#===============下面是alias配置=======================
#=====================================================

# add by feiyue 2018-11-26
# alias for subl
# 添加subllime的快速启动命令subl
alias subl="'/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl'"

# add by feiyue 2018-12-29
# alias for chrome
# 添加chrome的快速启动命令chrome
alias chrome='open -a "/Applications/Google Chrome.app"'

# add by feiyue 2021-06-01
# 在mac下的ls设置
# ls -G 为mac下为ls配置颜色的选项,在linux下为--color=tty,而mac下无--color,有-G来以颜色区分
# alias ls='ls -G'
# alias ll='ls -l'
```

