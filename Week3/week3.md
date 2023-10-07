# Week3 Classification

## Motivations

This type of classification problem where there are only two possible outputs is called binary classification. Where the word binary refers to there being only two possible classes or two possible categories.

只有两个可能输出的分类问题 称为二元分类,其中 binary 一词是指只有两个可能的类或两个可能的类别。

![<img src="C:\Users\五三七\AppData\Roaming\Typora\typora-user-images\image-20231004154105331.png" alt="image-20231004154105331" style="zoom: 33%;" />](https://img-blog.csdnimg.cn/cb6c0da0d11c4080b89909d99ecb98cb.png)


0: false, benight, negative, absence ≠ bad

1: true, malignant, positive, presence ≠ good

![<img src="C:\Users\五三七\AppData\Roaming\Typora\typora-user-images\image-20231004154505926.png" alt="image-20231004154505926" style="zoom: 33%;" />](https://img-blog.csdnimg.cn/debd5f953a7b4292aad70c716562a688.png)


当额外添加例子的时候，线性回归拟合的决策边界会移动。

logistic regression逻辑回归，虽然名字带有回归，但作用是分类。



## Logistic regression

![<img src="C:\Users\五三七\AppData\Roaming\Typora\typora-user-images\image-20231004154826693.png" alt="image-20231004154826693" style="zoom: 33%;" />](https://img-blog.csdnimg.cn/e70d3d84103849259aa5f3dd03d9cba4.png)


S型函数：sigmoid function，有时叫做logistic function, 结果再0到1之间

![在这里插入图片描述](https://img-blog.csdnimg.cn/38629294f5364fa8871adc1660e170db.png)


f表示的是y是1的概率，1-f即是y是0的概率



## Decision boundary

![在这里插入图片描述](https://img-blog.csdnimg.cn/9db8076fdc4c49bfba66f12d0a7bf00e.png)


设置一个阈值，使得当f>这个阈值时，y预测为1；相反，y预测为0。

通常，这个阈值设置为0.5，即z=0的时候。

![<img src="C:\Users\五三七\AppData\Roaming\Typora\typora-user-images\image-20231004155746536.png" alt="image-20231004155746536" style="zoom: 33%;" />](https://img-blog.csdnimg.cn/0ed3aeebf12448d7915089066d612d9e.png)


决策边界：z=0时的线，边界两侧y=1或y=0

决策边界不一定是直线，多项式越高阶，决策边界越复杂。



## Cost function for logistic regression

![<img src="C:\Users\五三七\AppData\Roaming\Typora\typora-user-images\image-20231004160357977.png" alt="image-20231004160357977" style="zoom:33%;" />](https://img-blog.csdnimg.cn/736ab486105c4697a4a7dc03fbf2d55d.png)


使用方差成本函数，则f为逻辑回归函数时，不是凸函数，局部最小值不一定是全局最小值。

![在这里插入图片描述](https://img-blog.csdnimg.cn/f29786da34fd4027a555a7f32e6291b6.png)


定义损失函数如图，f的取值范围在0到1之间。

当真实值y是1，且f接近1时，L的值接近0，说明损失较小；相反，f接近0时，L的值趋向正无穷，说明损失非常大。

当真实值y是0，且f接近0时，L的值接近0，说明损失较小；相反，f接近1时，L的值趋向正无穷，说明损失非常大。

![<img src="C:\Users\五三七\AppData\Roaming\Typora\typora-user-images\image-20231004161340089.png" alt="image-20231004161340089" style="zoom:33%;" />](https://img-blog.csdnimg.cn/dafa93991ffb447fb46e5e13c2276552.png)


选择这种损失函数，总体成本曲线是凸的，即有且仅有一个最小值，最小值是全局最小值。

回归与分类的成本函数区别如下图，上面是回归函数的成本函数，下面是分类函数的成本函数：

![<img src="C:\Users\五三七\AppData\Roaming\Typora\typora-user-images\image-20231004161526916.png" alt="image-20231004161526916" style="zoom: 33%;" />](https://img-blog.csdnimg.cn/7a7256fbe4dd4642b87b8cfcd51e941b.png)




## Simplified Cost Function for Logistic Regression

![在这里插入图片描述](https://img-blog.csdnimg.cn/26692a56b3ad4afaad7793a8c98eb42e.png)




## Gradient Descent Implementation

![<img src="C:\Users\五三七\AppData\Roaming\Typora\typora-user-images\image-20231004162655788.png" alt="image-20231004162655788" style="zoom:33%;" />](https://img-blog.csdnimg.cn/5c85e00985004aba8e079c5643cf38ec.png)


逻辑回归的wi和b的导数形式上看起来和线性回归的导数，但f函数实际上不一样，一个是sigmoid函数，一个是线性函数



## The problem of overfitting

![<img src="C:\Users\五三七\AppData\Roaming\Typora\typora-user-images\image-20231004163005285.png" alt="image-20231004163005285" style="zoom:33%;" />](https://img-blog.csdnimg.cn/0b7b02fc03174f6f8c47b194241bf886.png)


underfit欠拟合，high bias高偏差，对训练案例也没办法很好地拟合

just right, generalization正则化，对训练案例比较好地拟合，并且对测试案例也可以很好地拟合

overfit过拟合，high variance高方差，对训练案例非常好地拟合，但对测试案例拟合很差



Our goal when creating a model is to be able to use the model to predict outcomes correctly for **new examples**. A model which does this is said to **generalize** well. 



![<img src="C:\Users\五三七\AppData\Roaming\Typora\typora-user-images\image-20231004163435722.png" alt="image-20231004163435722" style="zoom:33%;" />](https://img-blog.csdnimg.cn/1313e33c58544e98a57d8555dd50616b.png)




## Addressing overfitting

![在这里插入图片描述](https://img-blog.csdnimg.cn/e7e12511d0a94174908f3a96a675bfd6.png)


解决过度拟合的方法：

1. Collect more data

2. Select features  ——Feature selection 选择重要的、影响大的特征

3. Reduce size of parameters ——"Regularization"正则化

   

![在这里插入图片描述](https://img-blog.csdnimg.cn/4714ec23f15746f0b7fed6ccd73266fd.png)


## Cost function with regularization
![在这里插入图片描述](https://img-blog.csdnimg.cn/5b377019430f4309a5a4a8e178f07420.png)


令w3、w4乘以一个非常大的数加到 J 后面，这样当使 J 尽可能地小的时候，w3、w4的值就会变得非常小

more generally, the way that regularization tends to be implemented is if you have a lot of features, say a 100 features, you may not know which are the most important features and which ones to penalize. 

一般并不能提前知道哪个特征更重要，所以正则化就是把所有特征都做类似处理

![在这里插入图片描述](https://img-blog.csdnimg.cn/19dc092994fe49e98f840155b1f9d3d1.png)


正则化参数 λ ，与学习率α类似，需要选择一个适合的值。

当λ过小的时候，wj的值就会减小得少，对wj没有说明影响，仍然会过度拟合；当λ过大的时候，所有w的值都变得很小，此时 J 的值就接近常数b。

一般不会对b进行正则化

![在这里插入图片描述](https://img-blog.csdnimg.cn/11d9e1a849214bdf81c16d78981c3641.png)

如图，成本函数的表达式的左边一项称为均方误差项（成本），右边一项称之为正则化项。



## Regularized linear regression

正则线性回归：

![在这里插入图片描述](https://img-blog.csdnimg.cn/b5cb9e494a99426b9bcbfd844d02abf9.png)


为什么每次更新λ都会缩小参数w：

![<img src="C:\Users\五三七\AppData\Roaming\Typora\typora-user-images\image-20231004170215220.png" alt="image-20231004170215220" style="zoom:33%;" />](https://img-blog.csdnimg.cn/cc10e232b4c44cd3bcbece8bc7fc17a8.png)


导数计算过程：

![在这里插入图片描述](https://img-blog.csdnimg.cn/0ee1aa24a8924676ad39f6830ec166dd.png)




## Regularized logistic regression

正则逻辑回归的导数形式和线性回归的一样，不同的只是f的表达式
