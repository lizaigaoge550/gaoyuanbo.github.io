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
## 循环遍历一个文件夹下所有文件
```python
  for f in `ls $dir`
  do
  ....note: 文件路径为$dir'/'$f
  done
```

## 循环遍历一个文件夹下所有文件,并且按"/"切分字符串
```python
#!bin/sh
for file in filter_blank/*
do
    f=`echo $file | cut -d "/" -f 2`
    #echo $f
    python /home/liuxe/share/tools/text_pre/remove_punc.py $file /home/liuxe/share/dataset/medical_data/ws/ltp/topwords/filter_punc/$f
done
```
