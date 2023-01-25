# Low Dimensional Visualization

Arthor: Zhaojiacheng Zhou

## Menu

1. Multidimensional Scaling
2. Principle Component Analysis

### Multidimensional Scaling

- Function `pdist`

  - Grammar:  
      pdist(data,"distance")

  - Inputs:
    |data|"distance"|
    |---|---|
    |An m-by-n numeric matrix containing the data. Each of the m rows is considered an observation.|An optional input that indicates the method of calculating the distance or dissimilarity. Commonly used methods are "euclidean" (default), "cityblock", and "correlation".|

  - Outputs: A distance or dissimilarity vector containing the distance between each pair of observations.

- Function `cmdscale`

  - Grammar:  
      [x,e] = cmdscale(D)
  - Inputs: A distance or dissimilarity vector.
  - Output:
    |x|e|
    |---|---|
    |m-by-q matrix of the reconstructed coordinates in q-dimensional space. q is the minimum number of dimensions needed to achieve the given pairwise distances.|Eigenvalues of the matrix x*x'.|

- Function `pareto`

  Create a pareto chart to relative magnitudes of a vector in descending order.

### Principle Component Analysis

- Function `pca`

Example:  
`[pcs,scrs,~,~,pexp] = pca(data)`

- Inputs:
  |data|An m-by-n numeric matrix. The n columns correspond to n observed variables. Each of the m rows corresponds to an observation.|
  |---|---|
- Outputs:
  |pcs|A n-by-n matrix of principal components.|
  |---|---|
  |scrs|An m-by-n matrix containing the data transformed using the linear coordinate transformation matrix pcs (first output).|
  |pexp|A vector of length n containing the percentage of variance explained by each principal component.|
