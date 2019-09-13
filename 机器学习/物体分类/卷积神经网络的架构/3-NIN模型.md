对于卷积神经网络来说，其卷积化的过程就是使用线形滤波器对图像进行内积化计算，并在每个卷积化结束之后得到一个特征图。
- 卷积计算是分层进行的，较为前面的卷积抽取的浅层的特征，越往后的卷积抽取是越复杂的特征，有一个循序渐进的过程。
- NIN模型抛弃固有的模式，在低级阶段就使用抽取能力更强的模型去替代抽取能力较弱的卷积层，从而期望提升卷积网络的整体表达和辨别能力。
## 不同
- 卷积层采用【1,1】的卷积核，进行初级范围的全连接提取，从而加强线形特征，达到更高的抽象，泛化能力更强
- 取消最后进行分类的全连接层，采用的全局池化层来取代最后的全连接层，因为全连接层参数多且易过拟合。在最后一层加一层Average Pooling层进行模型的最终分类。
对于VGG来说，权重数据百分之八十都是全连接层构成。
## 结构示例
```py
#conv1
self.out_data = self.conv("conv1",self.imgs,48,11,11,4,4)#(?, 224, 224, 3)
self.out_data = self.batch_norm(self.out_data)
self.out_data = self.relu("relu",self.out_data)
self.out_data = self.conv("cccp1",self.out_data,48,1,1,1,1)#(?, 56, 56, 96)
self.out_data = self.relu("relu",self.out_data)
self.out_data = self.conv("cccp2",self.out_data,48,1,1,1,1)#(?, 56, 56, 96)
self.out_data = self.maxpool("pool1",self.out_data,2,2,2,2)#(?, 56, 56, 96)

#conv2
self.out_data = self.conv("conv2",self.out_data,72,5,5,1,1) #(?, 28, 28, 96)
self.out_data = self.batch_norm(self.out_data)
self.out_data = self.relu("relu",self.out_data)
self.out_data = self.conv("cccp3",self.out_data,72,1,1,1,1)#(?, 28, 28, 256)
self.out_data = self.relu("relu",self.out_data)
self.out_data = self.conv("cccp4",self.out_data,72,1,1,1,1)#(?, 28, 28, 256)
self.out_data = self.maxpool("pool2",self.out_data,2,2,2,2)#(?, 28, 28, 256)

#conv3
self.out_data = self.conv("conv3",self.out_data,32,3,3,1,1)#(?, 14, 14, 256)
self.out_data = self.batch_norm(self.out_data)
self.out_data = self.relu("relu",self.out_data)
self.out_data = self.conv("cccp5",self.out_data,32,1,1,1,1)#(?, 14, 14, 128)
self.out_data = self.relu("relu",self.out_data)
self.out_data = self.conv("cccp6",self.out_data,32,1,1,1,1)#(?, 14, 14, 128)
self.out_data = self.maxpool("pool3",self.out_data,2,2,2,2)#(?, 14, 14, 128)

#conv3
self.out_data = self.conv("conv4",self.out_data,1024,3,3,1,1)#(?, 7, 7, 128)
self.out_data = self.batch_norm(self.out_data)
self.out_data = self.relu("relu",self.out_data)
self.out_data = self.conv("cccp7",self.out_data,1000,1,1,1,1)#(?, 7, 7, 2)
self.out_data = self.relu("relu",self.out_data)
self.out_data = self.conv("cccp8",self.out_data,1000,1,1,1,1)#(?, 7, 7, 2)

print("here shape is :", self.out_data.get_shape())
self.out_data = self.avg_pool("avgpool",self.out_data,7,7,2,2)
```
