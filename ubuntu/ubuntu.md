# Ubuntu16.04 刷机文档

# 前言

​	本文档涉猎Ubuntu16.04（某些功能也适用于其他Ubuntu版本）刷机，包括系统的一些配置，常用软件的安装，以及开发环境的搭建。	

##操作事项
* 软件中心换源：系统设置 -> 软件和更新 

* 中文目录更换为英文目录

  > 打开终端，在终端中输入命令:
  >
  > export LANG=en_US
  >
  > xdg-user-dirs-gtk-update
  >
  > 在弹出的窗口中询问是否将目录转化为英文路径,同意并关闭.
  >
  > 在终端中输入命令:
  >
  > export LANG=zh_CN
  >
  > 关闭终端,并注销或重启.下次进入系统,系统会提示是否把转化好的目录改回中文.选择不许要并且勾上不再提示,并取消修改.主目录的中文转英文就完成了~
  >
  > OK，现在你可以像linux迷一样痛快的使用cd命令了，cd /home/linuxmi/Downloads……
  >
  > 建议第二种
  >
  > http://www.linuxidc.com/Linux/2011-06/36903.htm

* 自动挂在分区

* 终端设置代理

  ` export http_proxy=http://127.0.0.1:1080 `

  ` export https_proxy=https://127.0.0.1:1080 `

* ​
## 常用软件
* 搜狗输入法

* chrome浏览器

  ```shell
  sudo wget http://www.linuxidc.com/files/repo/google-chrome.list -P /etc/apt/sources.list.d/
  wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
  sudo apt-get update
  sudo apt-get install google-chrome-stable
  # http://www.linuxidc.com/Linux/2016-05/131096.htm
  ```

* markdown编辑器，强推 typora

* typora

  ```shell
  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
  sudo add-apt-repository 'deb http://typora.io linux/'
  sudo apt-get update
  sudo apt-get install typora
  # https://www.typora.io/#linux
  # 如果是因为网络问题导致无法下载，请更换软件源
  ```

  ​

* 网易云音乐

* 微信

  ```shell
  # github地址 : https://github.com/geeeeeeeeek/electronic-wechat
  sudo apt-get install npm
  # Clone this repository
  git clone https://github.com/geeeeeeeeek/electronic-wechat.git
  # Go into the repository
  cd electronic-wechat
  # Install dependencies and run the app
  npm install && npm start
  ```

  ​

* lantern

  ```shell
  # https://github.com/getlantern/lantern
  ```

* 火狐下载插件，词典翻译插件

* chrome下插件

* pycharm

* sublime

* anaconda 

  **如果要安装opencv caffe，尽量不要装anaconda，总之尽量不要装anaconda了，坑很多 ，用自带的Python就好了 **

* cuda

  ```shell
  sudo dpkg -i cuda-repo-ubuntu1604-8-0-local-ga2_8.0.61-1_amd64.deb
  sudo apt-get update
  sudo apt-get install cuda
  nvidia-smi #查看显卡信息:如果无效，重启大法好
  cat /proc/driver/nvidia/version
  export PATH=/usr/local/cuda/bin:$PATH # 设置可执行文件路径			
  ```

* cudnn

  ```shell
  tar -zxvf cudnn-8.0-linux-x64-v5.1.tgz  
  cd cuda
  sudo cp lib64/libcudnn* /usr/local/cuda/lib64/
  sudo cp include/cudnn.h /usr/local/cuda/include
  cd /usr/local/cuda/lib64/
  # 更新软链接（其实本质上你cudnn5解压之后lib64文件夹下的3个文件中2个其实就是软链接）
  sudo rm -rf libcudnn.so libcudnn.so.5
  sudo ln -s libcudnn.so.5.1.10 libcudnn.so.5
  sudo ln -s libcudnn.so.5 libcudnn.so
  ```

* caffe

  ```shell
  # 不要安装anaconda，然后安装caffe的官方教程安装，一般不会有什么问题的
  # http://caffe.berkeleyvision.org/installation.html
  sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler
  sudo apt-get install --no-install-recommends libboost-all-dev
  # 安装cuda+cudnn，一般事先安装好
  # ATLAS OpenBLAS MKL 三者选一进行安装，caffe默认的为 atlas，所以一般选择安装atlas
  sudo apt-get install libatlas-base-dev
  # sudo apt-get install libopenblas-dev
  sudo apt-get install the python-dev # 强烈建议，不要装anaconda
  sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev
  # 安装opencv,建议安装opencv2.4.13
  cd caffe_home
  cp  Makefile.config.example Makefile.config
  vim Makefile.config # 进行配置，需要特别注意的一点是hdf5会报错，解决方案 ：
  # https://github.com/BVLC/caffe/issues/2690 
  # INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial/
  # LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib /usr/lib/x86_64-linux-gnu/hdf5/serial/
  make all -j8
  make test -j8
  make runtest -j8
  make pycaffe
  ```

* 安装opencv2.4.13（官方文档 http://docs.opencv.org/2.4/doc/tutorials/introduction/linux_install/linux_install.html）

  * 下载源代码
  * tar -zxvf 
  * ​


* okular pdf阅读器
## 开发编辑工具
* pycharm
* anaconda
* ​