# tensorflow
tensorflow tutorial

# 运行环境
IDE-pycharm

在anaconda构造的虚拟环境中运行

添加什么库的时候要在anaconda的虚拟环境中添加


## 使用keras进行训练时模型的搭建(fashion_mnist为例子)
### 数据导入和预处理
    import tensorflow as tf
    from tensorflow import keras
    
    fashion_mnist=tf.keras.datasets.fashion_mnist
    (train_images,train_labels),(test_images,test_labels) = fashion_mnist.load_data()
    
    数据归一化提高训练速度
    train_images = train_images/255
    test_images = test_images/255
### 模型搭建
    model = keras.Sequential([
    keras.layers.Flatten(input_shape=(28,28)),
    keras.layers.Dense(128,activation='relu'),
    keras.layers.Dense(10)
    ]
    )
### 模型编译
    model.compile(
    optimizer='adam',  #当前较好的优化器
    loss=tf.keras.losses.SparseCategoricalCrossentropy(from_logists=True)  #梯度往loss减小的方向
    )
### 开始训练
    model.fit(train_images,train_labels,batch_size=1000,epochs=10)
    #batch_size每1000张图片更新一次参数，epochs对数据集进行10轮训练
### 模型评估
    model.evaluate(test_images,test_labels,verbose=2)
    #verbose 表示显示训练过程的进度 2是都可以看到 1是只看到进度条，0是什么都没有
    
    
    

