## 实例

```python
  iris = datasets.load_iris()
  parameters = {'kernel':('linear', 'rbf'), 'C':[1, 10]}
  svr = svm.SVC()
  clf = GridSearchCV(svr, parameters,scoring=make_scorer(metrics.f1_score)) #设置自己的scorer函数
  clf.fit(iris.data, iris.target)
  #返回 best_score_, best_params, best_estimator_
```

```python
  #讲解f-score函数
  metrics.f1_score(y_true, y_pred, average="binary")
  binary 是默认参数
  'macro' 选择这个然后修改源码 选择想要返回的那类的f值，默认是平均f值
```
