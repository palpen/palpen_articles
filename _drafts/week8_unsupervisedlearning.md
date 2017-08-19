
# Unsupervised learning

Week 8 covers materials on unsupervised learning, which are learning algorithms that do not use class labels. It covers two topics: an algorithm for detecting clusters (K-means clustering) and an algorithm for reducing the dimensions of your data (principal component analysis).

EXCERPT

## K-means clustering

K-means clustering is an algorithm for detecting clusters or groups in your data. The K refers to the pre-specified number of clusters that you want to detect in your data. It is an unsupervised learning algorithm because it doesn't require your examples to have labels to detect the clusters. Some application of the K-means algorithm given in the course include market segmentation and social network analysis. Perhaps it can also be used to identify categories in your data in order to label them.

The goal is to get from this

INSERT IMAGE BEFORE ALGO IS APPLIED

to this

INSERT IMAGE OF END RESULT

In the example above, it is easy enough to see that there are two clusters. But with data with a much larger set of features, it is harder to see. It is also not always the case that data organize themselves into obvious clusters

TSHIRT HEIGHT WEIGHT PICTURE

This is where a systematic approach for detecting clusters, which is what the K-means algorithm does, is useful.

### The algorithm

1. Choose the number of clusters K and randomly choose these K vectors. These initial K vectors will be the first vectors
2. Two substeps:

    i. Assign each example $x^{(i)}$ to one of the K-centroid it is closest to. Formally, for each $x^{(i)}$, choose among the K vectors that minimizes the square of their Euclidean distance: $\lVert x^{(i)}-\mu_{k} \rVert^{2}$
    ii. Following i., you will have  STOPPE HERE!!!

### Issues to consider and tips for application


## Principal component analysis



### Issues to consider and tips for application

