
# Principal component analysis


<!--excerpt-->

Principal component analysis (PCA) is a dimension reduction algorithm. The dimension of ones data is given by the number of measurement types for each training example. For example, your dataset may---for a given observation---contain information on income, gender, level of education, years of work experience, etc. If there were a total of 10 of these measurements for each person in the data, then the vectors containing this information for each individual are said to be 10 dimensional. The goal of PCA is to transform the data in a way that reduces the dimensions of these vectors while minimizing the loss of information (explained below). We reduce the dimension of our data to save storage space, increasing the speed of our learning algorithms, and to allow the visualization of our data (which isn't possible beyond 3 dimensions.


## PCA algorithm
To reduce the dimension of data, PCA exploits the correlation among the various feature in the data. The extreme example would be one where two features are related by a constant factor (e.g. height in inches and in centimeters). In this case, one could reduce the dimension of the data by 1 with very little projection error. A more realistic example given in the course considers features measuring a pilot's enjoyment from flying an airplane and their skill. One would expect the two measures to be highly correlated. Using PCA can exploit this correlation by generating a new variable, z, that captures the information embodied by the two original features. This reduces the dimension of the data by 1 as we can now just use z in our learning algorithm instead of the pilot enjoyment and pilot skill features.

INSERT IMAGE PILOT SKILL / PILOT ENJOYMENT

The PCA algorithm 




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


### review of eigenvalues and eigenvectors

There are



### some latex formulas
* variance covariance matrix for demeaned data
$\boldsymbol{\Sigma} = \frac{1}{m}\sum\limits^{m}\limits_{i=1}(x^{(i)})(x^{(i)})^{T}$ where $x^{(i)}$ is an $nx1$ vector of features for observation $i$. The variance-covariance matrix can also be calculated by $\frac{1}{m} \boldsymbol{X^{T}}\boldsymbol{X}$ where $\boldsymbol{X}$ is the $mxn$ matrix with $m$ training examples and $n$ features.

* metric for variation retained
$\frac{\frac{1}{m}\sum\limits^{m}\limits_{i=1}\lVert x^{(i)} - x_{approx}^{(i)}\rVert ^{2}}{\frac{1}{m}\sum\limits^{m}\limits_{i=1}\lVert x^{(i)} \rVert ^ {2}}$