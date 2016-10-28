打乱顺序randperm(10) python : random.permutation

matlab不打印警告 warning off

matlab    怎么选择数组里两个元素的所有组合 nchoosek(list,k)

##Matlab weka的使用
* 把weka.jar考到matlab的java包中, 然后在两个classpath文件中(2016版 有两个classpath) 即写入
  $matlabroot/java/jar/weka.jar($matlabroot是matlab的根目录)
* 然后写程序调用weka时, 写上javaaddpath('weka.jar')这个jar和程序在同一目录下
* 特别注意的是 在运行的时候 weka可能会报找不到某个类下的某种方法, 这个是版本问题, 换成低版本的就好了(比如我的 3.6 -> 3.5)





