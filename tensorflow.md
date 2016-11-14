##lstm
 lstm 有三个重要的参数 batch, n_step, n_input, 通俗来说, batch 就是指样本数, n_step就是时间序列就是所谓的帧数, n_input 就是每帧的特征数.
 tensorflow 的lstm 先把输入x transpose成 [n_step,batch*n_input] 然后再split(0,n_step) split中0代表维度, n_step代表要切分多少个, 返回值是list
 以这个为例就是返回了一个list, 长度为n_step, 每个元素的维度是[batch*n_input], 这也就意味者有n_step 个cell
 
 ```python
 
 ```
 
 
 
 
