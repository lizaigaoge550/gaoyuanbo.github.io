##lstm
 lstm 有三个重要的参数 batch, n_step, n_input, 通俗来说, batch 就是指样本数, n_step就是时间序列就是所谓的帧数, n_input 就是每帧的特征数.
 tensorflow 的lstm 先把输入x transpose成 [n_step,batch*n_input] 然后再split(0,n_step) split中0代表维度, n_step代表要切分多少个, 返回值是list
 以这个为例就是返回了一个list, 长度为n_step, 每个元素的维度是[batch\*n_input], 这也就意味者有n_step 个cell
 
 ```python
 concat = _linear([inputs,h],4*self._num_units,True)
 i,j,f,o = array_ops.split(1,4,concat)
 new_c = (c*sigmoid(f+self._forget_bias) + sigmoid(i) * self._activation(j))
 new_h = self._activation(new_c) * sigmoid(o)
 ```
 
 但是tensorflow 的 bidirectional_dynamic_rnn(cell_fw,cell_bw,inputs,sequence_length,dytype)要求的输入不是上面的list, 而是一个三位数组          [batch,n_step,n_input], sequence_length 是实际的每个序列(每个样本有多少时序)的长度 np.ones(batch)*n_step, 还有一个重要的参数 time_major
如果是true, input是[n_step,batch,n_input]

lstm不可重复使用, 比如有n个hidden，每个hidden后，经过一个lstm 
```python
for h in hidden:
 ....
 ....
 lstm
```
这时会报 ./lstm/cell/W_0 distableed错误
 
 
 
 
 
 
 
