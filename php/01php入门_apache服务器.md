## php入门

### windows
- 下载phpstudy
- 开启apache2服务 : net start apache2 ,之后打开localhost查看网页内容
- apache2的相关配置文件 : httpd.conf 
  - Listen 监听的ip:端口
  - DocumentRoot: web的src存放地
  - Directory


### mac
- 自带php与apache2
- 启动apache服务: sudo apachectl start
- 配置文件: /etc/apache2/httpd.conf
- 开启自带的php: 在httpd.conf中将LoadModule php5_module libexec/apache2/libphp5.so 的注释给取消掉即可
- 
