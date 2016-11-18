MLP 主要有5个参数需要调节
1 hidden layer:
  * hinton:  add layers until you overfit and then use a regularizer, one hidden layer is sufficient for the large majority of problem
  * the optimal size of the hidden layer is usually between the size of input and size of output layer
  * use a large network and regulatisation, if you use regularisation then the nerwork become less important, you do need to fune the      regulatisation parameter properly
  * ![](http://latex.codecogs.com/gif.latex?\\frac{N_s}{\\alpha*(N_i+N_o)})  
     * ![](http://latex.codecogs.com/gif.latex?N_s)是样本数
     * ![](http://latex.codecogs.com/gif.latex?\\alpha)是scale parameter 2-10
     * ![](http://latex.codecogs.com/gif.latex?N_i)是样本特征数(input)
     * ![](http://latex.codecogs.com/gif.latex?N_o)是输出层节点数
     
