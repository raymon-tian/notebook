* **周志华的西瓜书还是写得太粗了**

* 协方差 与 相关系数
  https://www.zhihu.com/question/20852004

  协方差，从机器学习的视角出发，刻画了两个feature的相关性，进行可以判断样本特征中是否有着较为冗余的特征，譬如就性别的角度而言，设置男（0/1取值） 女(0/1取值) ，这样的做法必然存在着信息的冗余。

* N维向量空间的相关知识

  http://blog.codinglabs.org/articles/pca-tutorial.html

  https://zhuanlan.zhihu.com/p/21580949

* 线性无关 线性相关 线性表出

* 正交基 非正交基

* 向量A在基xxx下的坐标为xxxx，如何求在另一个基下的坐标

* N维向量空间的基底中N维向量的个数（N维向量空间的维数）

* N+1 个 N维向量 必然 线性相关

* **N维向量空间的一个基中的N维向量的个数一定是N，也就是说N维向量空间的维数必然是N**

* N维向量空间中基/正交基的个数

* **矩阵仅仅只是工具，一个矩阵，他本身不代表物理上，几何上等等的清晰含义，需要将其投入到具体的情境下去考虑他的某一行、列，或者对角线等等所具有的含义**

* 样本的相似性、样本特征之间的相似性，可以通过协方差来进行度量

* **n维向量可以等价表示为n维空间中的一条从原点发射的有向线段**，这个其实是在默认的基底的情况下阐述的。

* 向量空间的基，并非一定得是正交的

* 精确描述向量的前提是，该向量空间的基已经确定的前提下；说白了，向量就是要表示成基的线性组合。

* 点积的几何含义

* 矩阵相乘的一种物理解释：**两个矩阵相乘的意义是将右边矩阵中的每一列列向量变换到左边矩阵中每一行行向量为基所表示的空间中去**。

* 一般的向量都是指  **列向量**。

* 中心化：样本均值为0；归一化：样本均值为0，方差为1.

* 使用**矩阵、向量相乘**，一定要搞清楚相乘的意义何在。

* 标准差 方差 一般都是用来描述一维数据的。

* N维空间中的**一个平面**，**一条线段** 如何表示？

* **协方差矩阵这个东西，不仅仅可以用来度量特征之间的相关性，并且也可以用度量样本之间的相关性，说白了它就是一个度量高维数据相关性的一个工具，看你的用途，或者说看这个高维的数据是什么，是样本还是所有样本在每一特征上的取值，并不是仅仅只能用来度量特征之间的相关性。**


### 协方差矩阵（Covariance matrix）

- https://zh.wikipedia.org/wiki/%E5%8D%8F%E6%96%B9%E5%B7%AE%E7%9F%A9%E9%98%B5
- https://www.zhihu.com/question/24283387
- https://en.wikipedia.org/wiki/Covariance_matrix
- http://pinkyjie.com/2010/08/31/covariance/
- 对于数据集矩阵，NxM，N表示样本维度为N，M表示M个样本，协方差矩阵可以看成是研究样本之间相关性的工具。
- 想让两个样本/两种特征的相关性比较弱，那就使得其协方差比较小
- 求一个矩阵的协方差矩阵
- 协方差矩阵是计算不同维度之间的协方差，而不是计算样本之间的协方差；所以协方差矩阵的计算要看**数据矩阵**的表示情况，是一列表示一个样本，还是一行表示一个样本。
- 协方差矩阵并非是一种定死了的公式，因使用情况不同而计算方式不同，如何度量**样本之间的相关性/相似性**，**特征之间的相关性/相似性**。
- ​

### 正定矩阵



### 半正定矩阵



## 优化

### 拉格朗日乘子法

* 参考
  * http://www.cnblogs.com/mo-wang/p/4775548.html
  * ​

### KKT条件



## 对矩阵、向量的求导

* https://zhuanlan.zhihu.com/p/25063314
* https://zhuanlan.zhihu.com/p/24709748
* https://zhuanlan.zhihu.com/p/27523007
* matrix cookbook



## 矩阵

* **可逆矩阵**的概念都是针对方阵而言的。
* 奇异矩阵就是不可逆矩阵?



### 矩阵的迹

* ​



### 标量函数对矩阵/向量的求导

* https://zhuanlan.zhihu.com/p/24709748



## 奇异值分解

* ​



### PCA

http://blog.codinglabs.org/articles/pca-tutorial.html  (有一定的错误，但是写得确实不错)


