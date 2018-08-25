
### 安装mysql
- 1.官网下载MySQL Community Server的dmg安装文件: https://dev.mysql.com/downloads/mysql/
- 2.双击下载好的dmg文件,一路继续,最后会给你一个临时的mysql的root用户密码
- 3.在系统偏好设置中找到mysql,有个按钮开启mysql服务
  - 注:“Automatically Start MySQL Server on Startup” 为开机自启
- 4.在终端加入mysql相关的环境变量: 
  - vim ~/.bash_profile
  - 在最后加入 PATH=$PATH:/usr/local/mysql/bin ,之后:wq保存
  - source ~/.bash_profile
