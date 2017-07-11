# pytorch tutorial学习笔记
## 前言
* 该md文件，是针对 http://pytorch.org/tutorials/ 的学习笔记
## Tensor
### 初始化tensor
``` python
x = torch.Tensor(3,5) # 注意，不是 torch.tensor(3,5) tensor是torch模块根目录下的一个py文件，tensor.py
y =  torch.rand(3,5)
size = y.size()

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
### Function
* Variable 与  Function 相互关联，定义出来了一个计算图


## 遗留问题
* GPU上的Tensor如何传递到 内存
* **Variable上面的backward()函数中，参数 grad_output 到底是什么，grad_output的设置确实会改变求导的结果。**


    
    
    
    
    
    