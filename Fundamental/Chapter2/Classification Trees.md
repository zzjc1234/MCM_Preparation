# Classification Trees

Author: Zhaojiacheng Zhou

---

## Menu

1. Function `fitctree`

---

### Function `fitctree`

- Intro

    K-nearest neighbors (kNN) are distance-based classification models. Thus, they require all predictors to be numeric or all predictors to be categorical. Many data sets contain both numeric and categorical predictors. If you have mixed predictors, you cannot use all of your data with a kNN model.

    Decision trees, like kNN models, do not make any assumptions about the data, but they do allow a mixture of numeric and categorical predictors, given that they treat predictors independently.

- Grammar

  - Sample Code

    ```matlab
    mdl = fitctree(dataTrain,"faultCode");
    view(mdl,"mode","graph");
    evalModel(dataTest, mdl);

    mdlPruned = prune(mdl,"Level",2);
    view(mdlPruned,"mode","graph");
    evalModel(dataTest, mdlPruned);
    ```
