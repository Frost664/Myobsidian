#Tensorflow 
第一部分：[[]]
**要求python 3.7**，使用的是本机anaconda下创建的虚拟py37



```python
import tensorflow as tf  
  
w = tf.Variable(tf.constant(5, dtype=tf.float32))  
# w 初始值 5  可训练  
lr = 0.2  
# lr 学习率  
epoch = 40  
# epoch 循环迭代  
for epoch in range(epoch):  # for epoch 定义顶层循环，表示对数据集循环epoch次，此例数据集数据仅有1个w,初始化时候constant赋值为5，循环40次迭代。  
    with tf.GradientTape() as tape:  # with结构到grads框起了梯度的计算过程。  
        loss = tf.square(w + 1)  
        # 损失函数 loss (w+1)^2    grads = tape.gradient(loss, w)  # .gradient函数告知谁对谁求导  
  
    w.assign_sub(lr * grads)  # .assign_sub 对变量做自减 即：w -= lr*grads 即 w = w - lr*grads    print("After %s epoch,w is %f,loss is %f" % (epoch, w.numpy(), loss))  
  
# lr初始值：0.2   请自改学习率  0.001  0.999 看收敛过程  
# 最终目的：找到 loss 最小 即 w = -1 的最优参数w
```

此部分遇到的问题：
1. 安装的anaconda环境过高，搭配了python3.11，导致许多包不能使用
   需要修改python的版本，修改python版本的方法[^1]。
2. 在运行代码时，出现了<mark style="background: #FF5582A6;">*Original error was: DLL load failed: 找不到指定的模块“ 的解决办法*</mark>，此问题说的是未能找到相应的包。可以用这个方法[^2]


[^1]:[详解Anaconda + 如何在Anaconda上更换python版本_anaconda切换版本_宇内虹游的博客-CSDN博客](https://blog.csdn.net/weixin_39278265/article/details/82982937)

[^2]:[Pycharm报错：“Original error was: DLL load failed: 找不到指定的模块“ 的解决办法_知识它难道硌你脑子吗的博客-CSDN博客](https://blog.csdn.net/weixin_40293250/article/details/114586887)


## 1.3 张量的生成

张量 ： 可以表示0-n阶数组   
![[Pasted image 20230901214554.png]]

## 1.4 TF2常用函数

![[Pasted image 20230901215324.png]]
![[Pasted image 20230901215433.png]]
![[Pasted image 20230901215534.png]]



	tf.one_hot
独热码

tf.argmax
返回张量沿指定维度最大值的索引

## 1.6 鸢尾花数据集读入
