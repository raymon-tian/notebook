# pytorch tutorial学习笔记
## 前言
* 该md文件，是针对 http://pytorch.org/tutorials/ 的学习笔记
## Tensor
### 初始化tensor
``` python
x = torch.Tensor(3,5) # 注意，不是 torch.tensor(3,5) tensor是torch模块根目录下的一个py文件，tensor.py
y =  torch.rand(3,5)
size = y.size()
x = torch.FloatTensor(3,5)
x = torch.randn(3,5) # 均值为0，方差为1
x = torch.ones(3,5)
```
### Tensor的shape
* size = x.size()
* torch的size是继承Python tuple的对象
* torh.Size([3,5])
* torch Size 的一个小细节 : 是否会去掉一个虚假的维度，这一点numpy也是一样的
``` Python
In [50]: x
Out[50]: 

 2  2  2  2  2
 2  2  2  2  2
 2  2  2  2  2
[torch.FloatTensor of size 3x5]

In [52]: x[:,0].size()
Out[52]: torch.Size([3])

In [53]: x[:,0:1].size()
Out[53]: torch.Size([3, 1])

```

### Tensor的操作
* element-wize 加法
``` python
# 语法1
x = torch.Tensor(3,5)
y = torch.rand(3,5)
r = x+y
# 语法2
r = torch.add(x,y)
# 语法3
r = torch.rand(3,5)
torch.add(x,y,result=r)
# 语法4
x = torch.ones(3,5)
y = torch.ones(3,5)
r = x.add(y)
```
* 其他
``` python
x = torch.randn(3,5)
x.fill_(0)

```
### Tensor 的  in-place 操作
* 所有的带有 _ 后缀的Tensor操作函数都将以in-place方式地改变Tensor : 
* 
``` python
x.add(y)
x.add_(y)
```
### Tensor 与 numpy 
* Tensor 就是为了使用 GPU，而对numpy的替代
* Tensor 与 numpy的索引方式一样
* 一个 Tensor 与  一个 numpy 一一对应，他们拥有共享的内存，改变一个就会改变另外一个
* 在CPU上的Tensor，除了CharTensor，都可以与numpy array实现互转
* Tensor 与 numpy array的互转
``` python
# Tensor ========> numpy array
a = torch.ones(5)
b = a.numpy()
# numpy array =====> Tensor 
b += 1
a = torch.from_numpy(b)

```
### GPU上的 Tensor
``` python
if torch.cuda.is_available():
	x = x.cuda()
	y = y.cuda()
	
```

## torch模块下子模块——autograd模块
### autograd概要
* 对pytorch中的NN而言，最为核心的模块
* autograd模块提供了对于Tensor所有操作的自动求导
* 是一种 **被运行定义** 的框架，i.e 反向传播的过程取决于你的代码是怎么运行的，所以可能就会出现不同次的迭代，不同的反向传播过程
*  Variable 是 autograd模块中最为核心的对象
### Variable
* Variable 与 Tensor的关系
	* 前者包裹了后者
	* 前者几乎支持定义在后者上的所有操作
	* Variable中的data成员就是一个Tensor
* Variable的三个核心属性
	* data : 其包裹的Tensor
	* grad : 关于这个的梯度
	* creator : 引用生成了该Variable的Function
* Variable.backward 的 疑问
	* 其中传入的参数到底是什么用
### Function
* Variable 与  Function 相互关联，定义出来了一个计算图

## torch.nn
### overview
* 是torch模块中的子模块：涉及pytorch中的所有关于神经网络的操作
* nn.Module 包含了许多层，其上的forword(input)得到网络的输出
* nn依赖autograd.Variable来定义模型，以及在其上求偏导数
* 一个典型的网络定义如下
``` python
import torch
from torch.autograd import Variable
import torch.nn as nn
import torch.nn.functional as F


class Net(nn.Module):

    def __init__(self):
        super(Net, self).__init__()
        # 1 input image channel, 6 output channels, 5x5 square convolution
        # kernel
        self.conv1 = nn.Conv2d(1, 6, 5)
        self.conv2 = nn.Conv2d(6, 16, 5)
        # an affine operation: y = Wx + b
        self.fc1 = nn.Linear(16 * 5 * 5, 120)
        self.fc2 = nn.Linear(120, 84)
        self.fc3 = nn.Linear(84, 10)

    def forward(self, x):
        # Max pooling over a (2, 2) window
        x = F.max_pool2d(F.relu(self.conv1(x)), (2, 2))
        # If the size is a square you can only specify a single number
        x = F.max_pool2d(F.relu(self.conv2(x)), 2)
        x = x.view(-1, self.num_flat_features(x))
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        x = self.fc3(x)
        return x

    def num_flat_features(self, x):
        size = x.size()[1:]  # all dimensions except the batch dimension
        num_features = 1
        for s in size:
            num_features *= s
        return num_features


net = Net()
print(net)
```
* 一般在 构造函数中定义 **具有可学习参数的层**，并且**一般仅仅是所需层的简单罗列，不涉及具体的前向传播以及bp**
* 在forward函数中定义 **前向传播过程**，即为数据的计算流，所以说，网络结构的真正定义是在forward函数中。
* 可以在forward函数中使用任意的Tensor操作函数
* net.parameters()：返回网络的所有可学习参数
* forward函数的输入以及输出都是 autograd.Variable
* **切记，卷积层中的可学习参数还有bias，不仅仅是weights，而且，一般bias的个数就等于卷积核的数目，一个卷积核对应一个bias**
* torch.nn仅仅支持mini-batch，不支持一个样本，也就是说torch.nn的输入必须是一个mini-batch的样本，如果你只有一个样本，那么请加上一个fake的batch维度
> input.unsqueeze(0)

## 使用pytorch训练一个分类器
### 将网络以及输入,gt转移到cuda
> net.cuda()
> inputs,labels = Variable(inputs.cuda()),Variable(labels.cuda())

## pytorch中的数据迭代
``` python
for batch_idx,(data,target) in enumerate(dataLoader):
    # if batch_idx == 0:
    print(batch_idx)
    print(data.size())
    print(target.size())
    

```
* 其中，data，target并非是一个sample，而是一个完整的batch；所以，data的第一个维度为 样本在该batch中的索引
## 遗留问题
* GPU上的Tensor如何传递到 内存
* **Variable上面的backward()函数中，参数 grad_output 到底是什么，grad_output的设置确实会改变求导的结果。**
好像grad_output一般设置的是ground-truth，所以与网络的output具有一样的shape
* API
	* torch.randperm




    
    
    
    
    
    