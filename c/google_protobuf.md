## 解析json文件
```c++
#include <fcntl.h>
#include <google/prorobuf/io/zero_copy_stream_impl.h>
#include <google/protobuf/text_format.h>
using google::protobuf::io::FileInputStream
using google::protobuf::Message
//读取文件
int fd = open(filename,O_RDONLY) //filename是一个指针
FileInputStream* input = new FileInputStream(fd)
google::protobuf::TextFormat::Parse(input,proto) //proto是一个Message的指针解析后的内容放到了这个指针所指的位置
```
