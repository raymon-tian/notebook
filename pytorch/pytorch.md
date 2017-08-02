# pytorch学习笔记
## pytorch包内容
```
In [1]: import torch

In [2]: help(torch)

NAME
    torch

FILE
    /home/wd/anaconda2/lib/python2.7/site-packages/torch/__init__.py

DESCRIPTION
    The torch package contains data structures for multi-dimensional
    tensors and mathematical operations over these are defined.
    Additionally, it provides many utilities for efficient serializing of
    Tensors and arbitrary types, and other useful utilities.
    
    It has a CUDA counterpart, that enables you to run your tensor computations
    on an NVIDIA GPU with compute capability >= 2.0.

PACKAGE CONTENTS
    _C
    _dl
    _tensor_docs
    _tensor_str
    _thnn (package)
    _torch_docs
    _utils
    autograd (package)
    backends (package)
    cuda (package)
    distributed (package)
    functional
    legacy (package)
    multiprocessing (package)
    nn (package)
    optim (package)
    serialization
    sparse (package)
    storage
    tensor
    utils (package)
    version

```
> import一个Python包的时候，包名后面可以追加的字符串，无非是来自于 1.__init__.py文件中定义的变量名 2.该包目录下的文件名 3.该包目录下子包的名字
	

```
In [5]: help(torch.Tensor) # Tensor 定义在 __init__.py文件中
Help on class FloatTensor in module torch:

class FloatTensor(torch._C.FloatTensorBase, torch.tensor._TensorBase)
In [6]: help(torch.tensor) # tensor 指的是 torch模块下的文件——tensor.py
NAME
    torch.tensor

FILE
    /home/wd/anaconda2/lib/python2.7/site-packages/torch/tensor.py
    ```
    
    
    
    
    
    