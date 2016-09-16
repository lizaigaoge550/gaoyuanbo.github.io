##字符串的替换

* replace(a,b) 用b替换a
* transplate(table,b)  table用 from string import maketrans maketrans('wav','doc') doc替换掉wav  b是要删掉的字符比如',' note maketrans 两个参数长度要一样 相当于{'w':'d','a':'o','v':'c'}相当于字典
* re.sub 比如说 hello 123 world 456 想把123  456 替换成222  re.sub('\d+',222,字符串)
参数：pattern repl(字符串或函数 函数的话参数是匹配的组) string

##读取txt 加载txt 读取docx 读取csv

* numpy
  * numpy.loadtxt(filename,delimiter)
  * numpy.save(file,arr)--> numpy.save(outfile,arr), numpy.load(outfile)
  * numpy.savez(file,*args,**kwds) 保存文件.npz格式  --> numpy.savez(outfile,x,y)--> x = numpy.load(outfile)['arr_0']
  * numpy.genfromtxt 可以执行 列的分隔符(delimter) delimter=3是代表每个元素长度为3 delimter=[4,3,2]代表第一行的每个元素长度4 ...
跳过行和选择的列 skip_header=3 跳过前3列 skip_footer=5 跳过后5列
usecols 来选择列 dtype选择数据类型
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

##pandas 删除行

假如DataFrame v有一列叫pid 有一个list 保留出现在list中的pid的那些行
v[v.pid.isin(list)]

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
* 统计个数 list.count()

##python 遍历文件的2中方法

* os.walk(root) 参数根目录 返回3个参数 第一个是路径，第二个是路径下面的目录，第三个是路径下面的非目录（也就是文件）
* os.listdir(root)  os.isfile()




