得益于Tensorflow社区的繁荣，诞生出许多高质量的元框架，如keras等等
使用元框架能够大大减少编写Tensorflow代码的工作量，方便开发者搭建网络模型，并且代码简单，可读性强。
## keras
高度封装，非常适合新手，代码更新速度快，示例代码丰富，社区比较完整，代码自动调用GPU运算。
- 模块化
- 极简主义
- 易扩展性
## keras模型
- Sequential模型
- 函数模型

```py
model = Sequential()
model.add()
model.add()
...
model.add()
model.compile(loss = '',optimizer = '',metrics = '')
model.fit()
model.evalute()#函数用来评估模型，输出测试集的损失值和准确率
model.predict()
```
## 模型的操作
- fit：训练
- evalute：评估模型，准确率，损失值
- predict:预测值
- save_model:保存模型
- load_model：加载模型
