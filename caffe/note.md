* 可执行文件 **caffe** 有4条命令，train test device_query time
 usage : ``` caffe train --solver solver.prototxt ```
 * ```solver.prototxt``` 中的信息，对应着 ```caffe.proto```中 ```SolverParameter```的message
 * prototxt，就是google protobuf  ```message```的文本显示形式；所以，凡是 prototxt中的字段信息都应该去caffe.proto中查找
 * ```lenet_train.prototxt```	中的字段信息对应 ```caffe.proto```中的```NetParameter```信息
 * protobuf可以有4个方面的信息
 	* ```.proto```文件的定义 : 包含了原始信息的定义
 	* ```.protobinary```文件：消息的二进制存储文件
 	* ```.prototxt``` 文件：消息的文本文件存储方式
 	* ```caffe.pb.cpp caffe.pb.h``` 访问消息的代码
 * ***万变不离其宗，本质就是BP，按照BP的思路去理解caffe,以及各种各样的DL框架***
 * 使用Python读取 caffe_pb.py中的信息；使用Python读取 prototxt文件信息
 * python 将 protobuf  消息存储为 二进制 以及 文本信息
 * 如何使用 Python 访问 ```.proto```文件
 * caffe的前向传播
 * caffe的反向传播
 * 自定义caffe c/c++层
 * 自定义caffe python 层
 * 3D U-net 实验
  * caffe 如何 使用 Python层