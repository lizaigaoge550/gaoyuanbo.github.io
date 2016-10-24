##用下面形式来拟合数据

![](http://latex.codecogs.com/gif.latex?y(x,w)=w_0+w_{1}x+w_{2}x^2...+w_{m}x^m = \\sum_{j=0}^{M}w_{j}x^j)

##最小化误差

![](http://latex.codecogs.com/gif.latex?E(w) = \\frac{1}{2}\\sum_{n=1}^{N}(y(x_n,w)-t_n)^2)  

## 根均方误差RMS

![](http://latex.codecogs.com/gif.latex?E_{RMS}=\\sqrt{\\frac{2E(w^*)}{N}})

M的阶数越高越会出现过拟合现象，通过使用一种贝叶斯，过拟合问题可以避免。从贝叶斯参数的数量超过数据点数量的情形，没有任何难解之处。在一个贝叶斯模型中，参数的有效数量会自动根据数据集的规模调节
防止过拟合增加一个惩罚项

![](http://latex.codecogs.com/gif.latex?\\frac{1}{2}\\sum_{n=1}^{N}(y(x_n,w)-t_n)^2+\\frac{\\lambda}{2}||w^2||)

sum rule:

![](http://latex.codecogs.com/gif.latex?p(x)=\\sum_{Y}p(x,y))

product rule:

![](http://latex.codecogs.com/gif.latex?p(x,y)=p(y|x)p(x))

贝叶斯定理右侧的量p(D|w) 有观测数据集D来统计, 可以被看成参数向量![](http://latex.codecogs.com/gif.latex?p(w|D)=\\frac{p(D|W)p(w)}{p(D)}) w的函数
被称为似然函数，它表达了在不同的参数向量下w下, 观测数据出现的可能性的大小。注：似然函数不是w的概率分布，并且它关于w的积分并不一定等于1

posterior & likehood * prior

频率学家的观点:

w被认为是一个固定的参数, 它的值由某种形式的估计来确定，这个估计的误差通过考察可能的数据集D的概率分布得到

贝叶斯的观点：

只有一个数据集D(即实际观测到的数据集)，参数的不确定性通过w的概率分布来表达即w不是一个固定的参数

高斯分布:

![](http://latex.codecogs.com/gif.latex?N(x|\\mu ,\\sigma^2 )=\\frac{1}{(2\\pi\\sigma^2)^{\\frac{1}{2}}}exp(-\\frac{1}{2\\sigma^2}
                                                                                                            (x-\\mu)^2))

方差的倒数 ![](http://latex.codecogs.com/gif.latex?\\beta=\\frac{1}{\\sigma^2}) 被叫做精度. 分布的最大值叫众数，对于高斯分布, 众数与均值相等


![](http://latex.codecogs.com/gif.latex?p(x|\\mu,\\sigma^2)=\\sum_{n=1}^{N}N(x_n|\\mu,\\sigma^2))
极大似然估计

![](http://latex.codecogs.com/gif.latex?\\ln^{p(x|\\mu,\\sigma^2}) = -\\frac{1}{2\\sigma^2}\\sum_{n=1}^{N}(x_n-\\mu)^2-\\frac{N}{2}\\ln^{\\sigma^2}-\\frac{N}{2}\\ln^{2\\pi})

经过求导后 ![](http://latex.codecogs.com/gif.latex?\\mu_{ML}=\\frac{1}{N}\\sum_{n=1}^{N}x_n)

![](http://latex.codecogs.com/gif.latex?\\sigma^{2}_{ML}=\\frac{1}{N}\\sum_{n=1}^{N}(x_n-\\mu_{ML})^2)
