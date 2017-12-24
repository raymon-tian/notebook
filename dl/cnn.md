### CNN 中感受野的理解以及计算

#### 参考

* http://www.cnblogs.com/objectDetect/p/5947169.html

#### 感受野

* 最后的输出特征图中的一个1x1（2d情况）的像素，仅仅由输入图像中的某一块区域决定，那么原始图像中的这一块区域就是所谓的感受野

* 1) It is the size of the area of pixels that impact the output of the last convolution.

  2) For each convolution and pooling operation, compute the size of the output. Now find the input size that results in an output size of 1x1. Thats the size of the receptive field

* 第一层卷积层的输出结果的感受野就是第一层卷积层卷积核的大小

#### 计算公式

> **RF = 1 #待计算的feature map上的感受野大小**
> **　　for layer in （top layer To down layer）:**
> **　　　　RF = ((RF -1)\* stride) + fsize**

* 从最后的输出开始，倒推着计算，思路就是：**在得到输出特征图相对于倒数第n层的感受野的前提下，求输出特征图相对于倒数第n+1层的感受野，直到求得输出特征图相对于输入图像的感受野**
* 为什么是RF-1？ 因为要得到n个卷积结果，只需要滑动n-1次即可

