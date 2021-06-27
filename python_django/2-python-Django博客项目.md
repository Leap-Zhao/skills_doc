# python-Django博客项目

参考: [https://github.com/liangliangyy/DjangoBlog](https://github.com/liangliangyy/DjangoBlog)

## 1 项目安装

1. clone项目: git clone git@github.com:liangliangyy/DjangoBlog.git  并 cd进入
2. 安装依赖 (pip install知识参考其它部分内容) [99-pip相关知识.md](../python/99-pip相关知识.md) 
```bash
# 1. 先查看自己的pip版本(此项目要用python3 & pip3.x)
➜  djangoweb cd DjangoBlog
➜  DjangoBlog git:(master) pip -V
pip 10.0.1 from /Users/feiyue/Applications/minicode2/lib/python2.7/site-packages/pip (python 2.7)
➜  DjangoBlog git:(master) python3 -m pip -V
pip 21.1.2 from /Library/Python/3.7/site-packages/pip (python 3.7)
➜  DjangoBlog git:(master) pip3 -V
pip 21.1.2 from /Library/Python/3.7/site-packages/pip (python 3.7)
➜  DjangoBlog git:(master) pip3.7 -V
pip 21.1.2 from /Library/Python/3.7/site-packages/pip (python 3.7)
# 2. 通过pip install -Ur 安装依赖 (pip install -h查看帮助)
# -U, --upgrade : Upgrade all specified packages to the newest available version. The handling of dependencies depends on the upgrade-strategy used.
# -U、 --upgrade(升级)  将所有指定的包升级到可用的最新版本。依赖关系的处理取决于所使用的升级策略。
# -r, --requirement <file> :Install from the given requirements file. This option can be used multiple times. 
# -r、 --requirement<file> (依赖<文件名>) 从给定的需求文件安装。此选项可以多次使用。
pip install -Ur requirements.txt -i https://mirrors.aliyun.com/pypi/simple
```

3 
