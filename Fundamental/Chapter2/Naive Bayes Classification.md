# Naive Bayes Classification

 Author: Zhaojiacheng Zhou

 ---

## Menu

1. Naive Bayes

---

### Naive Bayes

- Intro

    kNN models and decision trees do not make any assumptions about the distribution of the underlying data.

    If we assume the data set comes from an underlying distribution, we can treat the data as a statistical sample. This can reduce the influence of the outliers on our model.

    A naïve Bayes classifier assumes the independence of the predictors within each class. This classifier is a good choice for relatively simple problems.

- Grammar

  - Sample Code

    ```matlab
    mdlNB = fitcnb(dataTrain,"faultCode","DistributionNames",dists);
    ```

- Related [link](https://www.bilibili.com/read/cv4119540/)
