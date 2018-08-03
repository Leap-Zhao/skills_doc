## php入门

### windows
- 下载phpstudy
- 开启apache2服务 : net start apache2 ,之后打开localhost查看网页内容
- apache2的相关配置文件 : httpd.conf 
  - Listen 监听的ip:端口
  - DocumentRoot: web的src存放地
  - Directory
- apache2的虚拟主机的配置文件 : conf/vhost.conf
  - 1.配置win下的hosts文件 
    - C:Windows\System32\drivers\etc\hosts (IP地址在前,空格,域名)
  - 2.配置apache的配置文件 : NameVirtualHost , Include conf/vhost.conf
  

### mac
- 自带php与apache2
- 启动apache服务: sudo apachectl start
- 配置文件: /etc/apache2/httpd.conf
- 开启自带的php: 在httpd.conf中将LoadModule php5_module libexec/apache2/libphp5.so 的注释给取消掉即可
- mac下apache的虚拟主机(Virtual hosts)配置文件与windows有所不同:  /private/etc/apache2/extra/httpd-vhosts.conf

### 目标
- 1.能够下载并使用apache服务器
- 2.会开启/关闭apache服务器
- 3.能自己配置2个虚拟主机
