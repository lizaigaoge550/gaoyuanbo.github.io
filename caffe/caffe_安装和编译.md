## 下载caffe
  * sudo git clone https://github.com/BVLC/caffe.git

## 安装第三方库
  * sudo apt-get install libatlas-base-dev
  * sudo apt-get install libprotobuf-dev
  * sudo apt-get install libleveldb-dev
  * sudo apt-get install libsnappy-dev
  * sudo apt-get install libopencv-dev
  * sudo apt-get install libboost-all-dev
  * sudo apt-get install libhdf5-serial-dev
  * sudo apt-get install libgflags-dev
  * sudo apt-get install libgoogle-glog-dev
  * sudo apt-get install liblmdb-dev
  * sudo apt-get install protobuf-compiler

## 安装opencv
  * cd caffe
  * sudo git clone https://github.com/jayrambhia/Install-OpenCV
  * cd Install-OpenCV/Ubuntu
  * sudo sh dependencies.sh
  * cd 2.4
  * sudo sh opencv2_4_10.sh
  
##配置运行环境
  * sudo vi /etc/ld.so.conf.d/caffe.conf
  * /usr/local/cuda/lib64
  * sudo ldconfig
  
## 编译caffe
  * cd ~/caffe
  * sudo cp Makefile.config.example Makefile.config
  * 修改Makefile.config 将USE_CUDNN注释号去除 :=1
  * make all 
  


