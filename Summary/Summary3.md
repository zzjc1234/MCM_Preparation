# Summary3

Author: Zhaojiacheng Zhou

由于整理自matlab英语课程，如果发现中英文有出入，请以英语版本为准

---

## Menu

1. Introduction
2. Cross Validation
3. Reducing Predictors - Feature Transformation
4. Reducing Predictors - Feature Selection

---

### Introduction

![slide1](src/slide1.jpg)
保留一部分数据用于验证模型拟合新数据的效果是一个好的尝试。但不同的分割可能会导致损失估计的改变。

![slide2](src/slide2.jpg)
每个算法都有可以修改的属性值，以提高性能。如何为数据集找到最佳属性值？

![slide3](src/slide4.jpg)
更简单的模型更容易解释，计算效率更高，不容易过度拟合。如何在不牺牲性能的前提下简化模型?

![slide4](src/slide4.jpg)
这章介绍的技术：

- 改进模型精度估计
- 降低模型复杂性
- 训练更精确的模型

---

### Cross Validation

- Intro

    评估模型性能的一个简单方法是将数据分为用于训练模型的子集和用于测试的子集: 用训练集拟合模型，然后使用测试集计算损失。

    ![CV-pic1](src/introImage1.png)

    当你想要选择最好的学习算法或方法时，你可以计算每种方法的损失，并选择损失最小的方法。

    但是，损失是根据数据的特定子集计算的。学习算法可能在特定子集上表现良好，但不能很好地推广到其他数据。

    通过使用交叉验证可以减少对特定测试子集的模型评估的影响。

    交叉验证背后的思想是多次重复模型评估过程。每次，该过程使用不同的训练和测试子集，并将模型拟合到训练集，并使用相应的测试集计算损失。

    ![CV-pic2](src/introImage2.png)

- 算法（k-fold cross validation)

    1. 将数据随机分为k个子集
    2. 将其中一个子集作为验证集，其余作为训练集
    3. 重复k次
    4. 计算loss的平均值

- 重要参数
  - k值

- 使用

  1. 创建CVpartition
  2. 使用CVpartition创建model
  3. 计算k-fold Loss

- Sample Code

    ```matlab
    cvpt = cvpartition(T.faultCode,"KFold",5)
    mdl=fitcdiscr(T,"faultCode","CVPartition",cvpt);
    kfLoss=kfoldLoss(mdl)
    ```

---

### Reducing Predictors - Feature Transformation

- Intro

  机器学习问题通常涉及具有数百或数千个预测因子的高维数据。

  例如:

  - 面部识别问题可能涉及数千个像素的图像，每个像素都可以被视为一个预测因子。
  - 预测天气可能涉及分析数千个地点的温度和湿度测量数据。

  学习算法通常是计算密集型的。减少预测因子的数量可以显著降低计算时间和内存消耗。

  此外，减少预测因子的数量会导致更简单的模型，更容易解释，通常泛化效果更好。

  Feature Transformation通过对观测变量的坐标空间进行变换来减少预测因子

- 算法（PCA)

  主成分分析(PCA)将一个n维特征空间转化为一个新的n维正交分量空间。这些成分是根据数据中解释的变化来排序的。  
  转换后的变量包含与原始数据相同数量的信息。然而，假设数据包含一定数量的噪声，包含解释方差的最后百分之几的分量很可能代表噪声而不是信息。  
  主成分分析可通过丢弃超出一个选定的解释方差阈值主成分来降维。

  主成分本身没有物理意义。然而，线性变换的系数表明了各变量在主成分中的贡献。  
  例如，如果第一主成分的系数分别为0.8、0.05和0.3，则第一个变量的贡献最大，其次是第三个和第二个变量。

- 可视化

  帕累托函数可以用来可视化由主成分解释的方差

  可以使用`biplot`来可视化任意两个主成分（通常为解释了数据中最大的方差的两个主成分）

  ![biplot](src/biplot1.png)

  可以使用heatmap（热力图）来可视化每个变量对主成分的贡献

  ![heatmap](src/heatmapPlotDefault.png)

  主成分分析可以独立于对应变量进行。然而，当数据的队友变量具有多个类别(例如，true和false)时，主成分分数的平行坐标图可能很有用

  ![parellelcoord](src/parallel.png)

- 使用

  1. 标准化数据（使用zscore）
  2. 将标准化后的数据作为pca的输入
  3. 绘制帕累托图
  4. 寻找能解释要求的百分比的方差（eg.99%)需要多少个主成分
  5. 使用找到的主成分创建模型
  6. 计算loss

- Sample Code

  ```matlab
  T{:,1:end-1}=zscore(T{:,1:end-1});
  [pcs,scrs,~,~,pexp]=pca(T{:,1:end-1});
  pareto(pexp)
  pos=find(cumsum(pexp)>=99,1);
  CVpt=cvpartition(T.faultCode,"KFold",10);
  mdl=fitcnb(PCApreds,T.faultCode,"CVPartition",CVpt);
  mdlLoss=kfoldLoss(mdl);
  ```

---

### Reducing Predictors - Feature Selection

- Intro