# Hierarchial Clustering

Author: Zhaojiacheng Zhou

---

## Menu

1. Function `linkage`
2. Function `dendrogram`

---

### Function `linkage`

- Description

    You can use the linkage function to encode a tree of hierarchical clusters from a set of observations.

- Grammar

    Z = linkage(data)

### Function `dendrogram`

- Description

    You can use the dendrogram function to visualize the hierarchy of a binary cluster tree.

- Grammar

        dendrogram(Z);

### Fucntion `cophenet`

- Description

    The Cophenetic correlation coefficient quantifies how accurately the tree represents the distances between observations. Values close to 1 indicate a high-quality solution.

- Grammar

        ccc = cophenet(linkages,distances)
