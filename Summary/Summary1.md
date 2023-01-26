# Summary1

Author: Zhaojiacheng Zhou

由于整理自matlab英语课程，如果发现中英文有出入，请以英语版本为准

---

## Menu

1. Low Dimensional Visualization
2. k-Means Clustering

---

### Low Dimensional Visualization

- PCA and CMD
  - Introduction

    PCA(Principle Component Analysis)和CMD(Classical Mutidimensional Scaling)是常用的多变量分析方法

  - 应用场景

    PCA和CMD可以在保证不失去大量信息的情况下对多变量数据or矩阵进行降维处理

  - 详细说明
    - CMD  
      CMD通常需要先计算观察值（observations）的成对距离（pairwise distance）从而生成相异度向量（dissimilarity vector)再计算重构后的矩阵（记重构后的矩阵为x）以及x*x'的本征值e。可以使用本征值e来确定对x中的点的低维近似是否提供了数据的合理表示。如果前p个特征值显著大于其余的特征值，则这些点被前p维(即x的前p列)很好地近似
    - PCA  
      PCA主成分分析的机理主要是是将原来很多具有相关性的一系列指标(p个指标)重新组合成一组较少个数的互不相关的综合指标来代替原来的指标。利用挑选的一组合适的权重来得到一个原随机变量的主成分[[link](https://anl.sjtu.edu.cn/mcm/docs/name/主成分分析PCA)]

      - 重要参数：  
        1. 原始数据：m行（观察值）n列（变量）
        2. Principal component coefficients(主成分系数）：p*p矩阵，每一列包含一个主成分相关系数。
        3. Principal component scores（主成分得分）：
        4. Principal component variances（主成分方差）：
        5. Hotelling’s T-Squared Statistic（霍特林T$^2$统计量）: A statistical measure of the multivariate distance of each observation from the center of the data set.
        [[link1](https://online.stat.psu.edu/stat505/lesson/7/7.1/7.1.15)]
        [[link2](T-squared-Test.pdf)]
        6. explained（解释方差占总方差的百分比）:Percentage of the total variance explained by each principal component
        7. mu(估计的均值):Estimated means of the variables in input data
      - 应用：  
        1. 使用explained（解释方差占总方差的百分比）绘制 Pareto chart（帕累托图）以判断哪几个principle component的contribution比较大，确定后续研究对象
        2. 确定研究的principle component之后绘制散点图或者运用聚类进行分类

---

### k-Means Clustering
