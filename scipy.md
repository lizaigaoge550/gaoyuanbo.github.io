## 获取以一个集合内，以一个点为圆心，半径为r 的所有点
  ```python
  import scipy.spatial as spatial
    #all 是全部数据集
    
    point_tree = spatial.cKDTree(all)
    #x是圆心,r是半径,返回的值是索引
    points_index = point_tree.query_ball_point(x,r)
    
    points = all[np.array(points_index,dtype=int),:]
  ```
## 计算欧氏距离
```python
  from scipy.spatial import distance
  distance..euclidean(poin_2t,point_1)
  ```
  
![](http://latex.codecogs.com/gif.latex?\\frac{\\partial J}{\\partial \\theta_k^{(j)}})





