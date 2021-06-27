# python虚拟环境- virtualenv安装和使用

如果python项目A想用一套环境,python项目B想用另一套环境,而且环境之间相互间隔,就需要用虚拟环境来实现

## 1 virtualenv

安装: pip install virtualenv

基础使用:

```bash
# 查看virtualenv命令
➜  ~ which virtualenv
/Users/feiyue/Library/Python/3.7/bin/virtualenv
# 创建虚拟环境文件夹djenv
➜  ~ mkdir djenv
➜  ~ cd djenv
➜  djenv
# 初始化虚拟环境
➜  djenv virtualenv ./
created virtual environment CPython3.7.3.final.0-64 in 593ms
  creator CPython3macOsFramework(dest=/Users/feiyue/webroot/djangoweb/djenv, clear=False, no_vcs_ignore=False, global=False)
  seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/Users/feiyue/Library/Application Support/virtualenv)
    added seed packages: pip==21.1.2, setuptools==57.0.0, wheel==0.36.2
  activators BashActivator,CShellActivator,FishActivator,PowerShellActivator,PythonActivator,XonshActivator
# 单独的python && pip环境
➜  djenv ls
bin        lib        pyvenv.cfg
➜  djenv cd bin
➜  bin ls
activate         activate.fish    activate.xsh     pip              pip3             python           python3.7        wheel-3.7        wheel3.7
activate.csh     activate.ps1     activate_this.py pip-3.7          pip3.7           python3          wheel            wheel3
# 激活此虚拟环境
➜  bin source activate
(djenv) ➜  bin ls
activate         activate.fish    activate.xsh     pip              pip3             python           python3.7        wheel-3.7        wheel3.7
activate.csh     activate.ps1     activate_this.py pip-3.7          pip3.7           python3          wheel            wheel3
# 虚拟环境生效
(djenv) ➜  djenv which python3
/Users/feiyue/webroot/djangoweb/djenv/bin/python3
(djenv) ➜  djenv which pip3
/Users/feiyue/webroot/djangoweb/djenv/bin/pip3
# 退出虚拟环境(任意位置即可)
(djenv) ➜  ~ deactivate
➜  ~
```

进阶使用:

```shell
# 指定虚拟环境的python版本
virtualenv ./ --pyhon=pyhon3.6   
```

## 2 virtualenvwrapper


virtualenvwrapper是virtualenv的扩展管理包，用于更方便管理虚拟环境，它可以做：

1. 将所有虚拟环境整合在一个目录下

2. 管理（新增，删除，复制）虚拟环境

3. 切换虚拟环境

安装: pip install virtualenvwrapper

基础使用: