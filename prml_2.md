如果模型的设计使用有限规模的数据集迭代很多次，那么对于验证数据会发生一定程度的过拟合, 因此保留一个第三方的测试集是很有必要的
这个测试集用来最终评估模型的表现(这个主要是用于调参，因为迭代很多次每次的参数可能都会越来越符合验证集，所以会发生过拟合.如果
交叉验证参数式固定的，不涉及到调参则交叉验证就够了).但是在许多应用中, 训练数据和测试数据都是有限的, 为了建立好的模型，我们想
使用尽可能多的数据进行训练. 然而如果测试集很小, 它对预测表现的估计就会有一定的噪声，解决这种情况的方法就是交叉验证

##信息熵
![](http://latex.codecogs.com/gif.latex?H[p] = -\\sum_{i}p(x_i)\\ln^{p(x_i)})


![](http://latex.codecogs.com/gif.latex?\\hat{H}=-\\sum_{i}p(x_i)\\ln^{p(x_i)}+\\lambda(\\sum_{i}p(x_i)-1))


对p(x_i)求导可得 ![](http://latex.codecogs.com/gif.latex?p(x_i) = \\frac{1}{M})时, 熵最大.

熵越大，越混乱同时越稳定，混乱状态是比较稳定的.

![](http://latex.codecogs.com/gif.latex?H[y|x] = -\\iint{p(x,y)\\ln^{p(y|x)}dxdy})

![](http://latex.codecogs.com/gif.latex?H[y,x] = H[y|x] + H[x])

H[x,y]是p(x,y)的微分熵

H[x]是边缘分布p(x)的微分熵

因此描述x和y所需的信息是描述x自己所需的信息加上给定x的情况下具体化y所需的额外信息.

相对熵(KL散度)

![](http://latex.codecogs.com/gif.latex?KL(p||q) = -\\int{p(x)\\ln^{\\frac{q(x)}{p(x)}}dx})

KL(p||q) >= 0 p(x) == q(x) kL = 0

互信息

![](http://latex.codecogs.com/gif.latex?I[x,y] = KL(p(x,y) || p(x)p(y)) =
-\\iint{p(x,y)\\ln^{\\frac{p(x)p(y)}{p(x,y)}}dxdy})

称为变量x和变量y之间的互信息.

互信息与条件熵之间的关系

I[x,y] = H[x] - H[x|y] = H[y] - H[y|x] 互信息可以看成是由于知道y的值而造成的x的不确定性的减少, 可以把p[x]看成p(x)的prior
p(x|y)看成是观察到新数据y后x的后验分布. 因此互信息表示一个新的观测y造成的x的不确定性的减少





