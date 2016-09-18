##spark 词袋模型

raw = 先抽取词

* 方法一：
  ```python
  dict = raw.flatMap(lambda x : x).distinct().collect()
  idx = 0
  all_terms_dict = {}
  for term in dict:
     all _terms_dict[item] = idx
     idx += 1
  ```
  
* 方法二
  ```python
  dict = raw.flatMap(lambda x : x).distinct().zipWithIndex().collectAsMap()
  ```

##spark 中两种操作transformation and action

  * transformation是得到一个新的RDD,方式很多,比如从数据源生成一个新的RDD,从RDD生成一个新的RDD
    * map 
    * filter
    * flatMap
    * mapPartitions
    * mapPartitionsWithSplit 
    * sample 
    * union 
    * distinct 
    * groupByKeey 
    * reduceByKey 
    * sortByKey 
    * join 
    * cogroup 
    * cartesian
  * action 是得到一个值，或者一个结果（直接将RDDcache到内存中）
所有的transformation都是采用的懒策略，就是如果将transformation提交是不会执行计算的，计算只有在action被提交时才被触发
    * reduce 
    * collect 
    * count 
    * first 
    * take 
    * takeSample 
    * saveAsTextFile 
    * saveAsSequenceFile 
    * countByKey 
    * foreach
  
  ##spark 缓存
 * 计算特别耗时
 * 计算链条很长
 * shuffle之后---shuffle从其他地方抓数据，要缓存下，如果后面阶段失败，从这个缓存阶段开始
 * checkpoint之前---一个作业执行完后，另一个作业开始前要checkpoint,缓存完这个作业的结果在进行下一个作业
 * 缓存不一定可靠因为缓存在内存中，checkpoint可靠。因为checkpoint在磁盘中
 * partition 会放在spark不同机器的节点上
 * partition一个特定的数据集合 大小默认是hdfs一个block的大小
 * Node local 本地磁盘
 * Process local 本地内存
 * Any 从其他机器shuffle来的数据
