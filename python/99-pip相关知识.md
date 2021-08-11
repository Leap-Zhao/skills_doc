# python-pip相关知识

参考 :

## 1 pip基础知识

pip

- pip freeze 查看环境已经安装的包及版本信息

```text
pip freeze > requirements.txt 即将整个python环境的依赖包生成到requirements.txt文件中
```

## 2 pip 在项目中的使用

一般python文件中都会有requirements.txt文件,中间记录此项目依赖的python第三方库.比如下面的requirements.txt

```text
coverage==5.5
Django==3.2.4
django-compressor==2.4.1
django-haystack==3.0
django-ipware==3.0.2
django-mdeditor==0.1.18
```

当项目拷贝到别的电脑上时,需要下载些依赖,这时候就需要用pip intall命令去安装

查看自己的pip版本

```bash
# 1. 先查看自己的pip版本(电脑中装了python2 && python3,就会有pip10.X && pip21.X)
➜  djangoweb cd DjangoBlog
➜  DjangoBlog git:(master) pip -V
pip 10.0.1 from /Users/feiyue/Applications/minicode2/lib/python2.7/site-packages/pip (python 2.7)
➜  DjangoBlog git:(master) python3 -m pip -V
pip 21.1.2 from /Library/Python/3.7/site-packages/pip (python 3.7)
➜  DjangoBlog git:(master) pip3 -V
pip 21.1.2 from /Library/Python/3.7/site-packages/pip (python 3.7)
➜  DjangoBlog git:(master) pip3.7 -V
pip 21.1.2 from /Library/Python/3.7/site-packages/pip (python 3.7)
```

通过pip install -Ur 安装依赖 (pip install -h查看帮助)

```bash
# 2. 通过pip install -Ur 安装依赖 (pip install -h查看帮助)
# -U、 --upgrade(升级)  将所有指定的包升级到可用的最新版本。依赖关系的处理取决于所使用的升级策略。
# -r、 --requirement<file> (依赖<文件名>) 从给定的需求文件安装。此选项可以多次使用。
# -i (可选项)  --index-url <url>  Python包索引的基URL（默认值http://mirrors.aliyun.com/pypi/simple/). 这应该指向符合pep503（简单存储库API）的存储库或以相同格式布局的本地目录。(注意,此默认地址可以修改)

# -U, --upgrade : Upgrade all specified packages to the newest available version. The handling of dependencies depends on the upgrade-strategy used.
# -r, --requirement <file> :Install from the given requirements file. This option can be used multiple times. 
# -i, --index-url <url>       Base URL of Python Package Index (default http://mirrors.aliyun.com/pypi/simple/). This should point to a repository compliant with PEP 503 (the simple repository API) or a local directory laid out in the same format.

# 一般用 -r就行
pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple

pip install -Ur requirements.txt -i https://mirrors.aliyun.com/pypi/simple

```

如何将一个python项目中的依赖生成到requirements.txt文件中去呢?

- 方法1(不推荐): 参考第一部分的 pip freeze > requirements.txt ,生成的是整个python项目的依赖,在任意位置都可以执行,不推荐使用
- 方法2: 使用 pipreqs 命令, 使用方法: pipreqs dir_path

```bash
# 安装pipreqs
➜  ~ pip install pipreqs
# 进入项目后,执行 
➜  mypro pipreqs ./
INFO: Successfully saved requirements file in ./requirements.txt
➜  mypro cat requirements.txt
thrift==0.13.0
```
