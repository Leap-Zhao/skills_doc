## 0.设置相关

### 0-1
  - 显示行号 :set nu 或 :set number
  - 不显示行号 :set nonu 或 :set nonumber
  - u是撤销你刚才做的动作
  - ctrl+r 是恢复你刚才撤销的动作

### 0-2 全局设置与用户设置
  - 用户设置文件为家目录下的.vimrc文件(没有时创建)  vim ~/.vimrc 添加设置内容后 source ~/.vimrc 
  - 全局设置文件为/etc/vimrc, 所以 sudo vim /etc/vimrc 添加设置内容后 source /etc/vimrc
  - 参照: https://blog.csdn.net/u013412790/article/details/51673333
 
### 0-3 设置内容
```shell
set hlsearch            "高亮度反白
set backspace=2         "可随时用退格键删除
set autoindent          "自动缩排
set ruler               "可显示最后一行的状态
set showmode            "左下角那一行的状态
set nu                  "可以在每一行的最前面显示行号啦！
set bg=dark             "显示不同的底色色调
syntax on               "进行语法检验，颜色显示。
```

## 1.复制,删除,剪切

### 1-1 删除
 - 删除当前行 dd
 - 删除5-10行  :5,10d
 - 删除光标位置到本行结尾 d$
 - 删除光标位置到本行开头 d0
 
### 1-2 剪切
  - 剪切5-10行到20行 :5,10m20

### 1-3 复制
  - 单行复制 在命令模式下，将光标移动到将要复制的行处，按“yy”进行复制；
  - 多行复制 在命令模式下，将光标移动到将要复制的首行处，按“nyy”复制n行；其中n为1、2、3⋯⋯
  - 粘贴4遍  4p
  
## 2.跳转

### 跳转字符
  - h,j,k,l 为 左 下 上 右,前面加数字n表示一次动的数
  - 向下5行  5j

### 跳转到指定行
  - 跳转到文件开头  gg  或 :1
  - 跳转到文件尾  G  或 :$
  - 跳转到指定行(比如第54行)  54G 或 :54
  
### 翻页
  - 向下翻半页  ctrl + d
  - 向上翻半页  ctrl + u
  - 向上翻一页  ctrl + b
  - 向下翻一页  ctrl + f

### 其它 
  - Ctrl+o 来回到之前修改的地方
  - Ctrl+i 会回退上面的跳动。


