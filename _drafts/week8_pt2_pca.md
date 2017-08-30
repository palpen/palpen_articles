
# Principal component analysis


<!--excerpt-->

Principal component analysis (PCA) is a dimension reduction algorithm. The dimension of ones data is given by the number of measurement types for each training example. For example, an observation in ones data for a given person may contain information on income, gender, level of education, years of work experience, etc. If there were a total of 10 of these measurements for each person in the data, then the vectors containing this information for each individual are said to be 10 dimensional. The goal of PCA is to transform the data in a way that reduces the dimensions of these vectors while minimizing the loss of information. Reducing the dimension of ones data can be useful for saving storage space, increasing the speed of ones learning algorithms, and data visualization.

## PCA algorithm
* find the k vectors that minimize the projection error that *span* the hyperplane onto which the data will be projected
* 


## Choosing the number of principal components
### Algorithm for choosing k

### How to go back from compressed to original data

Math:
* orthogonal linear transformation
* single value decomposition
* Variance covariance matrix
* orthogonal projection error

Resources:
* Andrew Ng ML youtube lecture 14 and 15
    - https://youtu.be/ey2PE5xi9-A?list=PLA89DCFA6ADACE599&t=2232
    - 

### short review of principal component analysis



### review of eigenvalues and eigenvectors

There are



### some latex formulas
* variance covariance matrix for demeaned data
$\boldsymbol{\Sigma} = \frac{1}{m}\sum\limits^{m}\limits_{i=1}(x^{(i)})(x^{(i)})^{T}$ where $x^{(i)}$ is an $nx1$ vector of features for observation $i$. The variance-covariance matrix can also be calculated by $\frac{1}{m} \boldsymbol{X^{T}}\boldsymbol{X}$ where $\boldsymbol{X}$ is the $mxn$ matrix with $m$ training examples and $n$ features.

* metric for variation retained
$\frac{\frac{1}{m}\sum\limits^{m}\limits_{i=1}\lVert x^{(i)} - x_{approx}^{(i)}\rVert ^{2}}{\frac{1}{m}\sum\limits^{m}\limits_{i=1}\lVert x^{(i)} \rVert ^ {2}}$