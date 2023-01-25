# k-Means Clustering

Arthor: Zhaojiacheng Zhou

## Menu

1. kmeans Function
2. kmeans Clustering

### kmeans Function

- Grammar: idx=kmeans(X,k)
- Inputs:

|X|k|
|---|---|
|Data, specified as a numeric matrix.|Number of clusters.|

- Outputs: Cluster indices, returned as a numeric column vector.
- Options:
  - Distance Metric:  
    By default, the euclidean distance is used to access the similarity between two observations. You can use other metrics such as correlation.

    Example:  
    g = kmeans(x,2,"Distance","correlation");

  - Replicates:  
    Another way to get optimum clustering is to perform the analysis multiple times with different starting centroids and then choose the clustering scheme which minimizes the sum of distances between the centroids and the observations (sumd).

    This can be done by using the "Replicates" property. The following command repeats the clustering 5 times and returns the clusters with lowest sumd.

    Example:  
    g = kmeans(x,2,"Replicates",5);
