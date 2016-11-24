##字符串的替换

* replace(a,b) 用b替换a
* transplate(table,b)  table用 from string import maketrans maketrans('wav','doc') doc替换掉wav  b是要删掉的字符比如',' note maketrans 两个参数长度要一样 相当于{'w':'d','a':'o','v':'c'}相当于字典
* re.sub 比如说 hello 123 world 456 想把123  456 替换成222  re.sub('\d+',222,字符串)
参数：pattern repl(字符串或函数 函数的话参数是匹配的组) string

##读取txt 加载txt 读取docx 读取csv

* numpy
  * numpy.prob(a) a = [1,2,3] 元素的乘积
  * numpy.loadtxt(filename,delimiter)
  * numpy.save(file,arr)--> numpy.save(outfile,arr), numpy.load(outfile)
  * numpy.savez(file,*args,**kwds) 保存文件.npz格式  --> numpy.savez(outfile,x,y)--> x = numpy.load(outfile)['arr_0']
  * numpy.genfromtxt 可以执行 列的分隔符(delimter) delimter=3是代表每个元素长度为3 delimter=[4,3,2]代表第一行的每个元素长度4 ...
跳过行和选择的列 skip_header=3 跳过前3列 skip_footer=5 跳过后5列
usecols 来选择列 dtype选择数据类型
  * numpy.savetxt()报错 foramt "%.18...." 这是因为不能保存3维数组, 要先转换成2维, 再保存.
* pandas
  * pandas.readcsv(filename)
    * 参数 header=None 不把第一行当作索引
    * index_col=False 不要用第一列作为索引
    * skiprows list or integer
    * nrows int
  * x1 = pandas.ExcelFile(filename)
name = x1.sheet_names
在解析x1.parse(name[..])
参数和csv类似
  * pandas.DataFrame.to_csv(dataframe,outputfile) note:要想把一个数组保存到csv 这个数组得先转化成DataFrame 用 pd.DataFrame(arr)
    * index = False 不要行名
    * header=False 不要列名
  * pandas.from_dict(dict,orient = "columns") orient = 'columns'是key作为列 'rows'key作为行
修改列名 DataFrame.columns = ['','']必须是list
  * pd.cut() 切分数据 pd.qcut() 也是切分数据 不同的是qcut(data,4)是按样本的4分位数进行切分得到大小基本相等的面元


##pandas 操作
 * 选择列 obj[val]  or obj.ix[:,val]
 * 选择行 obj.ix[val]
 * 同时选择行和列 obj.ix[val1,val2]
 * 属性 fill_value 填充缺失值 method = ffill or pad 前向填充 method = bfill or backfill 后向填充
 * df.fillna(val) 填充缺失值 可以是一个值，也可以是字典key是column名 value 是该列要填充的值

##pandas 删除行
 * 假如DataFrame v有一列叫pid 有一个list 保留出现在list中的pid的那些行
  v[v.pid.isin(list)]
 * df.drop(val1) 默认val1 是行的名字  drop(val2,axis=1) 是删除列
 * df.dropna() 只要行中出现NaN 删除该行,  参数 how='all' 行全部为NaN才删除  axis=1 表示对列操作.
 
##pandas 排序
 * series.sort_index() or   df.sort_index() 按index排序. 注:df可以加参数 axis=1表示按column排序; ascending=False 降序; by='val'。val用来指定   按某个列排序
 
 
 

保留出现在list中pandas的那些列 , df.loc[:,df.columns.isin(l)]

##os 执行 cmd命令

os.system(cmd) 例如: cmd命令(重命名命令)一般是 ren "fff" "dfdf" 文件名是有引号的 所以在python中这条命令应该是
''' ren "fff" "dfdf" '''

##移动dir to dir

* 导入包from distutils.dir_util import  copy_tree
* copy_tree(源文件夹，目的文件夹/源文件夹名/) note: 如果目的文件夹内没有原文件夹名先新建

##list 常用方法

* list.index(item)获取item的索引，如果出现多次，第一次
* del list[index] 删除index位置元素
* list.find(item) 类似与index
* 两个list相加 list1 + list2
* 添加元素 list.append() list.extend() 两者是不一样的 extend相当于flatMap
* 统计个数 list.count(item) 该item是list中的元素

##python 遍历文件的2中方法

* os.walk(root) 参数根目录 返回3个参数 第一个是路径，第二个是路径下面的目录，第三个是路径下面的非目录（也就是文件）
* os.listdir(root)  os.isfile()

##python正则表达式
* re.split('\\s+',字符串)
* 找到一个字符串中所有数字 re.findall('[0-9]+',string)

##pandas as pd 操作
* pd.read_csv().values仅仅只会忽略第一行，不会忽略第一列
* df.ix[] 用来选择行和列
* pd.Index(series).get_loc()获取位置

## pandas 合并数据集
* pd.merge(df1,df2) 默认是将重叠列的列名当作键
* pd.concat([df1,df2],axis=1) 可以选择方向合并

##numpy
* bincount来记录元素的个数. 例如bincount([0,0,1,1,2,3,4]) 结果[2,2,1,1,1]
* ravel把元素归成1行 例如s = [[2,3,4],[1,2,3]] np.ravel(s) [2,3,4,1,2,3]
* atleast_2d 把一个数组整成至少2维
* 合并数组 concatenate((a,b),axis=0) 0 相当于maltlab中的; 行合并 
  注意a,b 必须维度一致, 若a = [1,2] b = [[1,2],[2,3]]则出错 
* 向数组中插入一行或一列, np.r_ np.c_
  r_是行扩展 , np.r_['1,2',[1,2,3],[1,2,3]] '1,2'代表'n,m' m表示维度 axis=n, 相当于vstack(([1,2,3],[1,2,3])) => [[1,2,3],[1,2,3]]
  hstack 相当于 concatenate(axis=1) 如hstack(([1,2,3],[1,2,3])) => [1,2,3,1,2,3]注意这里是一维. r_相当于vstack 但是不同于vstack的是先用最小维   度 即 r_[[1,2,3],[1,2,3]] => [[1,2,3,1,2,3]] 若想变成[[1,2,3],[1,2,3]] r._['0,2'] 0代表行扩展, 2是2维
* 删除数组中某几行或几列 np.delete(数组,元素,axis)
* tile 复制元素
* where(condition,x,y) if condition x else y 返回的是tuple 类型
* savetxt 注意要把数组先整成int or float 否则可能汇报格式化的错误
* 随机数 random.choice
* 比较两个array是否相等(元素相同，类型相同) np.array_equal


##itertool
* chain('ABC','DEF') ---> A B C D E F
* from_iterable(['ABC','DEF']) ----> A B C D E F
* combinations('ABCD',2) -----> AB AC AD BC BD CD
* combinations_with_replacement('ABC',2) ------> AA AB AC BB BC CC
* compress('ABCDEF',[1,0,1,0,1,1]) ------> A C E F
* cycle('ABCD') -----> A B C D A B C D ......

## dict
* 字典排序 （sorted(wordlist.items(), key=lambda x:x[1],reverse=True)
  排序后每个元素是tuple类型
* collections 的 OrderedDict() 这个添加元素是按照元素的先后顺序添加的, 方法 popitem()弹出最后一个元素
  popitem(last=False)弹出第一个元素


##pandas Tuple
* 向tuple 中添加元素
  ```python
   a = (1,2,3,4)
   a = (5,)+a
   a = (5,1,2,3,4)
  ```

## string
* string.strip, lstrip, rstrip 
  S = '001100' , S.strip('0')--->'11', S.lstrip('0')---> '1100', S.rstrip('0')--->'0011'
