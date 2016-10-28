##jython
* 在官网上下载jython-installer.jar
* java -jar jython-installer.jar 进行安装

##Eclipse安装jython
* 先在Eclispe中安装Pydev插件方法
  * help -> install new software -> add 
   ![iamge](jython.png)
  * 重启后, windows-perfencens-在框中搜索Pydev 会出现配置(这里注意jython 高版本不行)
   搜索完后会出现一个对话框，点击Interpreter-Jython-> 在右边的框中点击new -> 不用写name, 点击下一个按钮选择上一步安装完的jython目录下的jython.jar文  件
   
##安装JyNI
* 下载源码，编译JyNI，可能会出现jni.h找不到。这个文件是jdk/include中的。locate jni.h 找到这个文件把它copy到报错的包中

   
  
  
  
