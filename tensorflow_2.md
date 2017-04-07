## tensorflow 排序
``` python
 _,index = tf.nn.top_k(data[j,:],k=5)
 w = tf.gather_nd(self.weights[i,:],tf.reshape(index,[5,1]))
 k =5 取前5个
 gather_nd 后面的rank 要比前面的shape[-1] 要大, 第一句是获取排序后下表, 后一句是取相同下表的w
```
## tensorflow select
* tf.select(condition,x,y) 满足条件就x ,不满足就y, 三者的shape要一样

## 计算梯度
```python
  tvars = tf.trainable_variables()
  grads = tf.gradients(self.loss,tvars)
  self.optimizer = optimizer.apply_gradients(zip(grads,tvars))
  获取某个变量的梯度
  grads = tf.gradients(self.loss,变量名)
```

## tf tile
* tf.tile(变量,大小) 注意大小和变量的rank一样
