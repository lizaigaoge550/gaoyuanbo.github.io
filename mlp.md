# MLP 主要有5个参数需要调节
## 1 hidden layer and hidden neutrons:
  * hinton:  add layers until you overfit and then use a regularizer, one hidden layer is sufficient for the large majority of problem
  * the optimal size of the hidden layer is usually between the size of input and size of output layer
  * use a large network and regulatisation, if you use regularisation then the nerwork become less important, you do need to fune the      regulatisation parameter properly
  * ![](http://latex.codecogs.com/gif.latex?\\frac{N_s}{\\alpha*(N_i+N_o)})  
     * ![](http://latex.codecogs.com/gif.latex?N_s)是样本数
     * ![](http://latex.codecogs.com/gif.latex?\\alpha)是scale parameter 2-10
     * ![](http://latex.codecogs.com/gif.latex?N_i)是样本特征数(input)
     * ![](http://latex.codecogs.com/gif.latex?N_o)是输出层节点数
  * ![](http://latex.codecogs.com/gif.latex?\\frac{2}{3}*N_i+N_o) 且小于 ![](http://latex.codecogs.com/gif.latex?2*N_i)
  * ![](http://latex.codecogs.com/gif.latex?\\sqrt{N_i*N_o})
  * 注意 data normalization

## 2 activation
  * 一般用relu
  * 但是数据不稀疏时考虑sigmoid
  
## 3 batch size
  * the lower it is, the training signal is , the higher it is, the longer it will take to compute the gradient for each step

## 4 epoch
  * 把数据分为train, valid, test
  * 初始化 epoch 一个很大的值
  * 当验证集效果最好时 ,break
  
## 关于neutrons, 也可以用pruning方法，看每步的权重，减去权重很小的节点 
     
## 初始化权重
 * sigmoid units 
   
   ![](http://latex.codecogs.com/gif.latex?U(-r,r), r= \\sqrt{\\frac{6}{N_i+N_o}})  
 * hyperbolic tangent units 
   
   ![](http://latex.codecogs.com/gif.latex?U(-r,r), r= 4\\sqrt{\\frac{6}{N_i+N_o}})  

## 判断结果是否过拟合
  * 看test set的accuracy and cross-entropy, 特点 accuracy 在经过一个高点后下降, cross-entropy 先下降, 然后上升.
    当accuracy and cross-entropy 在过拟合时, 而epoch不同以accuracy的为准.
  * 对比 train set 和 test set 的accuracy, 可以看到 train set的accuracy很高, test set的accuracy很低
  
    
    
