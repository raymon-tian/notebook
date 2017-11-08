# pytorch源码编译及阅读环境搭建

### 卸载原有版本

```shell
conda uninstall pytorch
pip uninstall torch
pip uninstall torch # run this command twice
```



### 克隆源代码

```shell
git clone --recursive https://github.com/pytorch/pytorch
```



### 编译安装

```shell
NO_CUDA=1 DEBUG=1 python setup.py build develop
```



### 参考

* https://github.com/pytorch/pytorch/blob/master/CONTRIBUTING.md
* https://github.com/pytorch/pytorch#from-source