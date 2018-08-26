## python2.7

### pip install MySQL-python

##### error1
- 在win下用pip安装MySQL-python,报如下错误:
```shell
error: Microsoft Visual C++ 9.0 is required (Unable to find vcvarsall.bat)
```
- 解决方法: 安装Microsoft Visual C++ Compiler for Python 2.7,网址: https://www.microsoft.com/en-us/download/confirmation.aspx?id=44266
- 参考网址: https://blog.csdn.net/hduxiejun/article/details/72577814
##### error2
- 解决完error1,又出现:
```shell
error: command 'C:\\Users\\zhaof\\AppData\\Local\\Programs\\Common\\Microsoft\\Visual C++ for Python\\9.0\\VC\\Bin\\amd64\\cl.exe' failed with exit status 2
```
- 解决方法: 下载MySQL_python-1.2.5-cp27-none-win_amd64.whl,pip install MySQL_python-1.2.5-cp27-none-win_amd64.whl
- 下载网址: https://www.lfd.uci.edu/~gohlke/pythonlibs/#mysql-python
- 参考网址: https://blog.csdn.net/u012882134/article/details/51934165/

## phthon3
