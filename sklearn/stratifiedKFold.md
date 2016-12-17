```python
self._iter_test_masks(x,y,groups)
   test_folds = self._make_test_folds(x,y)
   for i in range(self.n_splits):yield test_folds == i //把每次切分出去的索引至为True
   
def _make_test_folds(self,x,y=None,groups=None):
  y = np.asarray(y) //获取y
  n_samples = y.shape[0] //获取样本个数
  unique_y, y_inversed = np.unique(y, return_inverse=True) //得知有几类
  y_counts = bincount(y_inversed) //获得每类个数
  min_groups = np.min(y_counts) //获得最小类的个数
  if np.all(self.n_splits > min_groups):raise ValueError() //如果切分的数大于最小类的个数，异常
  per_cls_cvs = [KFold(self.n_splits, shuffle=self.shuffle,
                  random_state=rng).split(np.zeros(max(count, self.n_splits)))
            for count in y_counts] //把每个类切分为指定的份数 返回的是list类型，每个list的元素是generator类型
  test_folds = np.zeros(n_samples)
  for test_fold_indices, per_cls_splits in enumerate(zip(*per_cls_cvs)): //遍历每一个generator
            for cls, (_,test_split) in zip(unique_y,per_cls_splits): //然后在遍历和每一个类对应的splits
              cls_test_folds = test_folds[y==cls] //首先获取这类所有样本的位置
              cls_test_folds[test_split] = test_fold_indices //把该类的样本的test的值至为这次的切分数
              test_folds[y==cls] = cls_test_folds
 //如label = [0,0,1,1,1,1,0,0] splits = 4  return test_folds = [0,1,0,1,2,3,2,3]
 
              
```
