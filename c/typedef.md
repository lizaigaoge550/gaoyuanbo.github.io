## typedef 的主要应用有如下的集中形式：
* 为基本数据类型定义新的类型名
    * typedef unsigned int COUNT; 定义unsigned int 的别名为COUNT
    * typedef double AREA;定义 double 的别名为AREA
* 为自定义数据类型定义简洁的类型名称
    * typedef struct tagPoint{.......} Point 或者 typedef struct{......}Point
* 为数组定义简洁的类型名称
    * int a[10],b[10],c[10],d[10];等价于 typedef int INT_ARRAY_10[10]; \\ 
      INT_ARRAY_10[10] a[10],b[10],c[10],d[10]
* 为指针定义简洁的名称
    * typedef char * STRING; STRING csName={“Jhon”};
    * typedef int (*MyFUN)(int a，intb);
      
      ```c++
      int Max(int a，int b);
      MyFUN pMyFun;
      pMyFun= Max;
      ```
      
## typedef 和 \#define的区别
  * \#define AREA double 与typedef double AREA 可以达到相同的效果。但是其实质不同，
  
    \#define为预编译处理命令，主要定义常量，此常量可以为任何的字符及其组合，
    
    在编译之前，将此常量出现的所有位置，用其代表的字符或字符组合无条件的替换，
  
    然后进行编译。typedef是为已知数据类型增加一个新名称，其原理与使用int,double等保留字一致。
  
      
      
    
