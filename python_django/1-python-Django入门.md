# python-Django入门

入门文档参考: [菜鸟教程-Django](https://www.runoob.com/django/django-install.html)

[TOC]



## 1 Django-mac安装

1. 安装python & pip
2. 更新pip到最新
3. 使用pip安装Django
4. 判断Django是否安装成功

   ```bash
   # 2 更新pip到最新
   # -i https://pypi.tuna.tsinghua.edu.cn/simple 指定清华镜像源，下载速度更快。
   sudo python3 -m pip install --upgrade pip -i https://pypi.tuna.tsinghua.edu.cn/simple
   # 3 使用pip安装Django
   # 中间报这种错误为网络超时,重试即可: pip._vendor.urllib3.exceptions.ReadTimeoutError: HTTPSConnectionPool(host='pypi.tuna.tsinghua.edu.cn', port=443): Read timed out.
	sudo python3 -m pip install Django -i https://pypi.tuna.tsinghua.edu.cn/simple
   # 4 判断Django是否安装成功(import Django)
   ➜  ~ python3
   Python 3.7.3 (default, Apr 24 2020, 18:51:23)
   [Clang 11.0.3 (clang-1103.0.32.62)] on darwin
   Type "help", "copyright", "credits" or "license" for more information.
   >>> import django
   >>> django.VERSION
   (3, 2, 4, 'final', 0)
   >>> exit()
   ```

5. 其它安装办法参考: [菜鸟教程-Django](https://www.runoob.com/django/django-install.html)

## 2 Django创建项目

1. django-admin startproject 创建项目
2. pythhon3 manage.py runserver 执行项目
3. python manage.py migrate
4. 在浏览器打开http://127.0.0.1:8000/

```shell
# 1. django-admin startproject 创建项目
➜  djangoweb django-admin startproject djtest
➜  djangoweb ls
djtest
➜  djangoweb which django-admin
/usr/local/bin/django-admin
➜  djangoweb cd djtest
➜  djtest ls
djtest    manage.py
# pythhon3 manage.py runserver 执行项目
# 如果指定端口号,则 python3 manage.py runserver 0.0.0.0:8000
➜  djtest python3 manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.
June 12, 2021 - 04:00:35
Django version 3.2.4, using settings 'djtest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

查看项目目录结构如下:

```shell
➜  djangoweb cd djtest
➜  djtest ls
db.sqlite3 djtest     manage.py
➜  djtest tree
.
├── db.sqlite3
├── djtest
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-37.pyc
│   │   ├── settings.cpython-37.pyc
│   │   ├── urls.cpython-37.pyc
│   │   └── wsgi.cpython-37.pyc
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── manage.py

2 directories, 11 files
```

## 3 Django自身mvt实现简单项目

参考: [菜鸟教程-Django](https://www.runoob.com/django/django-install.html) 的创建第一个项目及之后的部分

djtest/djtest/views.py

```python
from django.http import HttpResponse
from django.shortcuts import render

def index(request):
    context = {}
    context['hello'] = 'this is index page'
    # 使用template页面,setting.py中TEMPLATES.DIRS中设置: 'DIRS': [os.path.join(BASE_DIR,'templates')]
    return render(request, 'index.html', context)

def default(request):
    return HttpResponse("this is default page")

def hello(request):
    return HttpResponse("hello world")
```

djtest/djtest/urls.py

```python
from django.contrib import admin
from django.urls import path
from django.conf.urls import url
from . import views

urlpatterns = [
    path('admin/', admin.site.urls),  # 项目自带
    url(r'^$',views.default), # 手动添加,default页面
    path('index/', views.index), # 手动添加,index首页
    path('hello/', views.hello), # 手动添加,hello页面
]
```

djtest/templates/index.html

```html
<!-- 这是演示template的作用,但是实际项目中一般不要这么做,而是使用static文件夹实现前后端分离 -->
<h1>{{hello}}</h1>
```

djtest/djtest/settings.py

```python
from pathlib import Path
# 导入os包
import os

# Build paths inside the project like this: BASE_DIR / 'subdir'.
BASE_DIR = Path(__file__).resolve().parent.parent
# 用户自定义STATICFILES_DIRS,动静分离时用,定义statics静态文件夹位置
STATICFILES_DIRS = [os.path.join(BASE_DIR,"statics")]
# ...中间settings.py文件自带部分略过
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR,'templates')],  # 用户自己添加,定义templats文件夹位置
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

## 4 vscode编辑python相关设置

### 4.1 相关插件

1. 通用插件
- 必装插件1: Chinese (Simplified) Language Pack for Visual Studio Code  (vs code中文语言包)
- 必装插件2: IntelliJ IDEA Keybindings (vs code 支持IntelliJ IDEA 快捷键)

2. python插件
- 必装插件3: Python extension for Visual Studio Code (vs code python扩展包-针对python项目)

3. nginx插件
- 必装插件4: nginx.conf (支持nginx语法亮和提示)
- 必装插件5: nginx-format (保存自动format更正nginx配置文件格式)

### 4.2 vscode其它设置

1. 如何在linux中添加vs code打开文件或文件夹的命令工具

   > 首先打开vscode软件。
   >
   > 同时按住`shift + command + P`打开命令面板。
   >
   > 找到`Install ‘code' command in PATH`，并执行。
   >
   > 那么就可以在终端执行命令了。

执行效果:

```shell
➜  djtest which code
/usr/local/bin/code
➜  djtest code /etc/hosts
```

## 5 动静分离实现一个django项目

这里使用bootstrap前端框架来实现

还以上面的default页面来体现

```python
# djangoweb/djtest/djtest/urls.py 中
path('index/', views.index),

# djangoweb/djtest/djtest/views.py 中
def index(request):
    return render(request, 'index.html')
  
# djangoweb/djtest/djtest/settings.py 中
import os
STATICFILES_DIRS = [os.path.join(BASE_DIR,"statics")]
STATIC_URL = '/static/'
INSTALLED_APPS = [
    'django.contrib.admin',
		# ... 其它apps
    'django.contrib.staticfiles',
]

# djangoweb/djtest/templates/index.html 从bootstrap示例中选择 bootstrap-3.4.1/docs/examples/dashboard/index.html
# 但是要更改原始index.html中引入的一些css和js文件的相对路径

# djangoweb/djtest/statics中放置要引入的css,js等文件,当然也可以自己加层路径,比如/djtest/statics/dist/css等
```

原bootstrap项目中的文件路径

```shell
➜  bootstrapweb tree bootstrap_example
bootstrap_example
├── assets
├── dist
│   ├── css
│   ├── fonts
│   └── js
└── examples
    └── dashboard
        ├── dashboard.css
        └── index.html
```

将index.html移到 djtest/templates/ 下, 将dist & assets 移到  djtest/statics下,并将dashboard.css 也移到 djtest/statics/dist/css下

现在的django项目djtest的statics/ 文件夹路径如下:

```bash
➜  djtest tree statics
statics
├── assets
└── dist
    ├── css
    │    ├── *.css    
    │    ├── dashboard.css
    ├── fonts
    └── js
        ├── *.css
```

在 djtest/templates/index.html中改动的引用css与js文件路径

```html
<!-- 原bootstrap项目中 href="../../dist/css/bootstrap.min.css" -->
<link href="/static/dist/css/bootstrap.min.css" rel="stylesheet">

<!-- 原bootstrap项目中 href="../../assets/css/ie10-viewport-bug-workaround.css" -->
<link href="/static/assets/css/ie10-viewport-bug-workaround.css" rel="stylesheet">

<!-- 原bootstrap项目中 href="dashboard.css" -->
<link href="/static/dist/css/dashboard.css" rel="stylesheet">

<!-- 原bootstrap项目中 href="../../assets/js/ie-emulation-modes-warning.js" -->
<script src="/static/assets/js/ie-emulation-modes-warning.js"></script>
```

此时我们已经可以通过http://127.0.0.1:8088/index/ 访问首页了, 如果想要通过自定义的域名访问, 则需要在/etc/hosts (mac或linux) 下修改 127.0.0.1的域名映射关系,此处我们将其映射到www.djtest.com中.

```tex
127.0.0.1	  localhost
127.0.0.1   www.djtest.com
```

最终实现效果:

![image-20210613110708047.png](https://i.loli.net/2021/06/13/ZRYyPGfglFp6LSM.png)

**总结: **

​       **实际上大家也能看明白,最终template/下的html文件中会将与statics/下的文件作为引用根路径(此根路径要加上/static,而不是/statics), 因此在html中引用相关的css与js文件中时,只需要将href指向 /static文件(实际是statics文件夹)即可.**

## 6 添加nginx反向代理

上一节我们最终实现了以 http://www.djtest.com:8000 (如果以8000端口起) 访问后台服务的话,如果我们想通过域名www.djtest.com不加端口号就直接访问的话(不加时默认使用的是80端口)需要怎么做呢?

需要用到nginx反向代理的功能,参考网址: [使用域名访问本地项目和nginx反向代理](https://blog.csdn.net/qq_29479041/article/details/107016992)

1. 前提: vs code nginx插件(上面已说过,这里再次说明)

- 必装插件: nginx.conf (支持nginx语法亮和提示)
- 必装插件: nginx-format (保存自动format更正nginx配置文件格式)

2. 前提: 本地hosts文件配置域名解析
   - 在/etc/hosts (mac或linux) 下修改 127.0.0.1的域名映射关系 

```tex
127.0.0.1   www.djtest.com
```

3. 在nginx配置文件nginx.conf中配置反向代理内容

   ```nginx
   worker_processes  1;
   error_log  logs/error.log;
   events {
   	# 支持的最大连接数为 1024
       worker_connections  1024;
   }
   
   http {
       include       mime.types;
       default_type  application/octet-stream;
       log_format  main  
       	'$remote_addr - $remote_user [$time_local] "$request" '
         '$status $body_bytes_sent "$http_referer" '
         '"$http_user_agent" "$http_x_forwarded_for"';
     
       access_log  logs/access.log  main;
       sendfile        on;
       # 设置客户端和服务端的超时时间
       keepalive_timeout  65;
   
      # 重点是serve的配置
       server {
           listen       80;
           server_name  www.djtest.com;
           access_log  logs/access.log main;
           location / {
               proxy_pass http://127.0.0.1:8000;
               proxy_connect_timeout 60s;
               proxy_read_timeout 60s;
            }
           error_page   500 502 503 504 404 /50x.html;
           location = /50x.html {
               root   html;
           }
       }
       include servers/*;
   }
   ```

4. nginx启动,并在浏览器执行 www.djtest,com/index

   ![截屏2021-06-19上午12.58.23.png](https://i.loli.net/2021/06/19/BKXvSthei8ApVNJ.png)

5. nginx原理

     ![截屏2021-06-19上午12.52.06.png](https://i.loli.net/2021/06/19/guSPwHqO9ZWeIb2.png)

  - 浏览器准备发起请求，访问http://www.djttest.com，但需要进行域名解析
  - 优先进行本地域名解析，因为我们修改了hosts，所以解析成功，得到地址：127.0.0.1
  - 请求被发往解析得到的ip，并且默认使用80端口：http://127.0.0.1:80
  - 本机的nginx一直监听80端口，因此捕获这个请求
  - nginx中配置了反向代理规则，将www.dj.com代理到127.0.0.1:8000，因此请求被转发
  - 后台系统的webpack server监听的端口是8000，得到请求并处理，完成后将响应返回到nginx
  - nginx将得到的结果返回到浏览器
