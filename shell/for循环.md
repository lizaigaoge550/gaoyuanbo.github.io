```shell
#!/bin/sh

%初始化ip
predix='192.168.9.'
%命令
cmd='pip install nltk --upgrade'
%初始化数据
ip_array=()
user='root'

%往数组里添加1-29的元素
for ((seq=4;seq<=29;seq++))
do
echo $predix$seq
ip_array+=($predix$seq)
done

%循环ip
for ip in ${ip_array[*]}
do
scp -r 'fenci' $user@$ip:'/home'
ssh $user@$ip $cmd
done

```
