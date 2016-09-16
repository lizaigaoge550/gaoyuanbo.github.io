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
  
  
