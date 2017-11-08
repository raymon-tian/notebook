# setuptools module 详解

## demo(Python module 的编写,安装,以及卸载)

### 编写

```shell
cd ~
mkdir demo
cd demo
vim setup.py
```

在 setup.py文件中输入

```python
from setuptools import setup, find_packages
setup(
    name = "demo_wd_buaa",
    version = "0.1",
    packages = find_packages(),
)
```

创建一个包

```shell
mkdir my_test_pack
cd my_test_pack
vim __init__.py
```

输入

```python
#!/usr/bin/env python
#-*- coding:utf-8 -*-

def test():
    print "hello world!"  

if __name__ == '__main__':
    test()
```

执行

```shell
cd ..
python setup.py bdist_egg
```

查看结果 : `tree`

```tx

├── build
│   ├── bdist.linux-x86_64
│   └── lib.linux-x86_64-2.7
│       └── my_test_pack
│           └── __init__.py
├── demo_wd_buaa.egg-info
│   ├── dependency_links.txt
│   ├── PKG-INFO
│   ├── SOURCES.txt
│   └── top_level.txt
├── dist
│   └── demo_wd_buaa-0.1-py2.7.egg
├── my_test_pack
│   └── __init__.py
└── setup.py
```

### 安装 

 ` cd .. pip install --user demo`

查看安装结果 : `pip list`

> demo-wd-buaa (0.1)

```shell
cd ~/.local/lib/python2.7/site-packages/demo_wd_buaa-0.1-py2.7.egg-info
tree
.
├── dependency_links.txt
├── installed-files.txt
├── PKG-INFO
├── SOURCES.txt
└── top_level.txt

0 directories, 5 files
cd ~/.local/lib/python2.7/site-packages/my_test_pack
tree
.
├── __init__.py
└── __init__.pyc

0 directories, 2 files

# 测试
ipython
In [1]: import my_test_pack

In [2]: my_test_pack.test()
hello world!
```

### 卸载

```shell
pip uninstall demo-wd-buaa
 Uninstalling demo-wd-buaa-0.1:
  /home/raymon/.local/lib/python2.7/site-packages/demo_wd_buaa-0.1-py2.7.egg-info
  /home/raymon/.local/lib/python2.7/site-packages/my_test_pack/__init__.py
  /home/raymon/.local/lib/python2.7/site-packages/my_test_pack/__init__.pyc
Proceed (y/n)? 
```

## 上述demo注意事项

* demo_wd_buaa-0.1-py2.7.egg-info 是与 my_test_pack 平行放置的
* import 的时候,不是  import demo_wd_buaa,而是import my_test_pack
* 卸载的时候不是 pip uninstall my_test_pack,而是 pip uninstall demo_wd_buaa

## 参考

* http://yansu.org/2013/06/07/learn-python-setuptools-in-detail.html

## 展望

* https://setuptools.readthedocs.io/en/latest/setuptools.html    setuptools 文档 **强烈推荐**

### setuptools 优点

* 纵然你的Python包部署的时候借助了setuptools,但是你的包本身不需要依赖于setuptools,setuptools独立于你的包仅仅是作为工具使用,因为`import setuptools`等的这些代码仅仅写在setup.py文件中,而你安装的包中是不会包含setup.py文件的.

* > you don’t have to include the entire setuptools package in your distributions.

* ​