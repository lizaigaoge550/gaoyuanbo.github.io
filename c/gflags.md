用于程序运行时参数的控制，
```C++
#include<gflags/gflags.h>
DEFINE_string(solver,"","The solver ....") #参数名, 默认值, 参数描述 --sovler=....

```
在主程序中用这个参数的值时 FLAG_slover
