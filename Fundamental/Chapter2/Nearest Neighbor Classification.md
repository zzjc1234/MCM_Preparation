# Nearest Neighbor Classification

Author: Zhaojiacheng Zhou

---

## Menu

1. Function `fitcknn`

---

### Function `fitcknn`

- Introduction

    Function `fitcknn` can create a knn model.

- Grammar

  - Sample Code

    ```matlab
    %Using the knn model with the the response variable fault code, and number of neighbor (k value) 7, the metric correlation and distance weight squared inverse
    mdlkNN = fitcknn(dataTrain,"faultCode", ...
    "NumNeighbors",7,...
    "Distance","correlation", ...
    "DistanceWeight","squaredinverse");
    ```
