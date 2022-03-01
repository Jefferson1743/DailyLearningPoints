# Inter-Series Attention Model for COVID-19 Forecasting

## 摘要 
区别于其他的方法统计学模型，本文提出了基于attention机制的模型，单纯依靠数据训练的一个模型。

整个过程主要包括两步：

1. Detrend
2. 模型
    1. 模型部分首先通过卷积获取多个特征之间的局部特征
    2. 通过卷积获取多个日期的发展之间的局部特征
    3. 将1、2两个部分的数据输入到attention中进去。
    4. attention输出的数据经过FFN层输出到预测。
    5. 模型中还使用了残差连接。