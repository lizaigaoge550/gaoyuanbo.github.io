## 安装nvidia驱动
* 在nvidia官网上下载, 显卡对应的驱动
* 如果是ssh 登上的 直接service lightdm stop, 如果是界面登录, 先进入tty(ctrl+alt+f1),在执行service lightdm stop
* 安装驱动,检验驱动是否成功安装 nvidia-smi

## 安装cuda8.0
* 官网上下载run文件
* 一步一步进行安装
* 配置环境变量 
  export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/extras/CUPTI/lib64"
  export CUDA_HOME=/usr/local/cuda
* 测试是否成功 nvcc --version

## 安装cudnn
* 官网上下载(这里需要先注册一个账号(lizaigaoge550@gmail.com)(wsnw2000))
* tar xvzf cudnn-8.0-linux-x64-v5.1-ga.tgz
  sudo cp cuda/include/cudnn.h /usr/local/cuda/include
  sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64  
  sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*

## 注意
 仅仅是把libcudnn的so, 拷贝过去会报 不能打开libsudnn.so这个文件的错误. 原因是libcudnn.so 其实是个软连接
 做法把/usr/local/cuda/lib64/libcudnn.so 以及 libcudnn.so.5都删掉(因为他们都是软连接)
 然后建立软连接
 ln -s libcudnn.so.5.1.0 libcudnn.so.5
 ln -s libcudnn.so.5 libcudnn.so
 
