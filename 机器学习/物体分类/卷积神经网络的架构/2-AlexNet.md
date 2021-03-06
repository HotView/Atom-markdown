AlexNet使用GPU对更多的数据进行处理，并且首次引入了Dropout层来处理过拟合以及使用ReLU替代sigmoid来作为激活函数。

AlexNet上一层完整的卷积层可能包括一层convlution，一层relu，一层pooling，一层normalization。
整个网络结构包括5层卷积层和三层全连接层，网络的最前端是输入图片的原始像素点，最后端的图片是分类结果。
## AlexNet
首先我们来看下神经网络的坚守者Hinton在2012年和他的学生Alex Krizhevsky设计的AlexNet，该模型拿到了当年ImageNet竞赛的冠军并从此掀起了一波深度学习的热潮。
![](picture/CNN基本类型-d76a3a88.png)
AlexNet主要由5个卷积层和3个全连接层组成，最后一个全连接层通过softmax最终产生的结果作为对于输入图片在1000个类别（ILSVRC图片分类比赛有1000个类别）上的得分。
#### AlexNet是第一个使用卷积神经网络在ILSVRC获得冠军的网络结构，它有如下几个特点：
1. 使用ReLU作为激活函数：为了加快深度神经网络的训练速度，AlexNet将传统神经网络神经元激活函数为f(x) = tanh(x)或 f(x) = (1 + e-x)-1改为f(x) = max(0; x)，即Rectified Linear Units（ReLUs）。从图1.可以看出，从一个含有4层卷积的神经网络上看，ReLUs相比tanh作为激活函数收敛速度要快上几倍。当训练误差同在25%时，ReLUs约5次迭代即可达到tanh迭代约35次的效果。
经过表1的分析可知，AlexNet有超过6千万的参数，虽然ILSVRC比赛有大量的训练数据，但仍很难完成对如此庞大参数的完全训练，从而导致严重的过拟合问题。AlexNet很巧妙地用下面两种方法处理这两个问题：
    1. 数据增强：在图像领域，最简单也最常用的避免过拟合的方法就是对数据集的增强。这里介绍几种数据增强的方法。
    1） 对原始图片做随机裁剪。如原始输入图片大小为256*256，那么训练时随机从256\*256的图片上裁剪224\*224的图片作为网络的输入。
    2） 找到原始图片RGB三个通道对应的主成分（PCA）
    3)另外还有一些常见数据增强的方法，如训练时对原始图片进行随机上下、左右翻转，平移，缩放，旋转等。
    2. 使用dropout：该想法一个是为了避免过拟合再一个是使用更有效的方式进行模型融合。具体方法是在训练时让神经网络中每一个中间层神经元以0.5的概率置为0。当某个神经元被置为0时，它便不会参与前向传播以及反向回传的计算。因此每当有一个新的图片输入就意味着网络随机采样出一个新的网络结构，而真正整个网络的权重一直是共享的。从感性的角度讲，dropout的存在强迫神经网络学习出更稳定的特征。预测时使用所有神经元但将其输出均乘以0.5。

2012年AlexNet使用8层神经网络已top1分类误差16.4%的成绩摘得ILSVRC的桂冠，2013年ZFNet在AlexNet基础上做了超参的调整，使top1误差降到11.7%并成为新的冠军。ZFNet将AlexNet第一个卷积层的kernel从11*11，stride为4改为7*7，stride为2；第三、四、五层卷积的kernel个数从384、384、256分别改为512、1024和512。2014年Simonyan和Zisserman设计了层次更深并且kernel更小的VGGNet。
