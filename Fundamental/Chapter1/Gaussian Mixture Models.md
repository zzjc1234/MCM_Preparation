# Gaussian Mixture Models

Arthor: Zhaojicheng Zhou

---

## Menu

1. Function `fitgmdist`
2. Function `cluster`

---

### Function `fitgmdist`

Function `fitgmdist` can fit several multidimensional gaussian (normal) distributions.

### Function `cluster`

Function `cluster` can cluster the data probabilically, by calculating each observation’s posterior probability for each component.

You can also return the individual probabilities used to determine the clusters.

### Sample Code of `fitgmdist` and `cluster`

```matlab
gm = fitgmdist(X,2);  %create the Gaussian Mixutre model
g = cluster(gm,X);  %cluster the data probabilically according to the model
[g,~,p] = cluster(gm,X);    %return the individual probabilities used to determine the clusters
```
