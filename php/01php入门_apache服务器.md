## php入门

### windows
- 下载phpstudy
- 开启apache2服务 : net start apache2 ,之后打开localhost查看网页内容
- apache2的相关配置文件 : httpd.conf 
  - Listen 监听的ip:端口
  - DocumentRoot: web的src存放地
  - Directory
- apache2的虚拟主机的配置文件 : conf/vhost.conf 或者 conf/extra/httpd-vhosts.conf
  - 1.配置win下的hosts文件 
    - C:Windows\System32\drivers\etc\hosts (IP地址在前,空格,域名)
  - 2.修改apache的配置文件httpd.conf : 将Include conf/vhost.conf 或 Include conf/extra/httpd-vhosts.conf的注释去掉
  - 3.编辑http-vhost.conf文件,内容例子如下:
  ```xml
  <VirtualHost *:80>
    ServerAdmin webmaster@dummy-host.example.com
    DocumentRoot "D:\phpStudy\PHPTutorial\practice\project1"
    <Directory "D:\phpStudy\PHPTutorial\practice\project1">
      Options Indexes FollowSymLinks
      AllowOverride All
      Order allow,deny
      Allow from all
    </Directory>
    ServerName www.leapzhao.com
    ServerAlias www.leapzhao.com
    ErrorLog "D:\phpStudy\PHPTutorial\practice\project1\error.log"
    CustomLog "D:\phpStudy\PHPTutorial\practice\project1\access.log" common
  </VirtualHost>
  ```
  - 4.重启httpd服务

### mac
- 自带php与apache2
- apache服务命令行:
  - 启动服务器：sudo apachectl start
  - 停止服务器：sudo apachectl stop
  - 重启服务器: sudo apachectl restart
- 配置文件: /etc/apache2/httpd.conf
- 开启自带的php: 在httpd.conf中将LoadModule php5_module libexec/apache2/libphp5.so 的注释给取消掉即可
- mac下apache的虚拟主机(Virtual hosts)配置文件与windows有所不同:  /private/etc/apache2/extra/httpd-vhosts.conf
  - 1.修改/etc/hosts,设置域名和ip对应
  - 2.在httpd.conf中把Include /private/etc/apache2/extra/httpd-vhosts.conf的注释取消掉
  - 3.编辑httpd-vhosts.conf文件 vim /etc/apache/extra/httpd-vhosts.conf,内容例子如下
  ```xml
    <VirtualHost *:80>
      ServerAdmin webmaster@xiaohua.com
      DocumentRoot "/Users/yourname/Dev/xiaohua.com"
      ServerName xiaohua.com
      ErrorLog "/Users/yourname/Dev/xiaohua.com/error_log"
      CustomLog "/Users/yourname/Dev/xiaohua.com/access_log" common
      <Directory "/Users/yourname/Dev/xiaohua.com">
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Require all granted
      </Directory>
    </VirtualHost>
  ```
  - 4.重启httpd服务 sudo apachectl restart
  - 参考: [https://jingyan.baidu.com/article/c85b7a646ad2a8003bac95f5.html](https://jingyan.baidu.com/article/c85b7a646ad2a8003bac95f5.html)

### 目标
- 1.能够下载并使用apache服务器
- 2.会开启/关闭apache服务器
- 3.能自己配置2个虚拟主机
