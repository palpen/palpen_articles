
# Support vector machines (SVM)

Week 7 covers the support vector machine (SVM) algorithm. This is the last supervised learning algorithm covered in the course.

EXCERPT

SVMs is hailed to be a very powerful learning algorithm for non-linear classification. In its basic form, the algorithm looks for the line that most "cleanly" separates the different classifications in the data. By cleanly, it finds the line with the largest margin on either side. Because of this, the SVM algorithm is also called a **large margin classifier**.

Consider the example below

<a href="{{site.url}}/img/wk7_8.png">
<img src="{{site.url}}/img/wk7_8.png" width="350" height="150"/>
</a>

In the figure, the line the most *cleanly* separates the classes X from O is the negatively sloped line running between the two classes. The two nearly vertical line also separates the two classes, but they are not the decision boundary that is optimal.

The SVM algorithm uses a cost function that have a similar structure to the cost function of the logistic regression. In the logistic regression the cost function include the log of the sigmoid function and the log of 1 minus the sigmoid function. For SVM, these terms are replaced by a piecewise function that looks like the following depending on the value of y (they are the dark blue line tracing the corresponding function in logistic regression)

<a href="{{site.url}}/img/wk7_2.png">
<img src="{{site.url}}/img/wk7_2.png" width="350" height="150"/>
</a>

<a href="{{site.url}}/img/wk7_3.png">
<img src="{{site.url}}/img/wk7_3.png" width="350" height="150"/>
</a>

The structure of these terms of the cost function in SVM is what gives rise to the large margin characterization of the decision boundary.

SVMs can model very complex non-linear decision boundaries. In the logistic regression case, we can model non-linear decision boundaries by using higher-order polynomials features. The drawback of this approach is that it can become computationally expensive to train the model, especially in cases where the data has a very rich set of features. Another complicated decision boundary could be a case where you cannot split the two classes with one continuous line.

The SVM algorithm gets around this by using a kernel to map the two data points--a training example and a landmark--to some value representing the similarity between the two. The kernel used in the course is the [Gaussian kernel](https://en.wikipedia.org/wiki/Radial_basis_function_kernel) (also called the Radial basis function kernel).

I still don't understand the mathematical justification for the kernel trick. Based on my reading of outside sources, the kernel is applied to project the data to a different feature space. This is important especially if the data is non-linearly separable. In such a case, the kernel trick in SVM allows the projection of the data into a space where it will be linearly separable. I will definitely need to revisit this in the future to understand the details.

## Parameters to choose when using SVM

There are two parameters to tune when using SVM with the Gaussian kernel: C and $\sigma$. C is just the inverse of the regularization parameters, $\lambda$. With greater C, $\lambda$ must be small. This means we are more likely to overfit (greater variance). Conversely, a small C imply a large $\lambda$. This makes it more likely to underfit (greater bias).

$\sigma$ is the Gaussian kernel parameter controlling the speed at which the value of the function changes as you move away from its peak. A smaller $\sigma$ results in a steeper slope around the peak. Conversely, a higher $\sigma$ results in a flatter kernel function. 

[here] (http://haohanw.blogspot.ca/2014/03/ml-how-sigma-matters-in-svm-rbf-kernel.html)

## Practice tips when using SVMs



The two parameters that needs to be exogenously given are the regularization parameter C and the kernel parameter SIGMA




What is the major advantage of SVM over other learning algorithms?

## SVMs in Practice

#### advantages

#### disadvantages



### Questions:
- Why is the hypothesis equal to 1 when theta * X is greater than zero? (first video)? Why isn't it greater than or equal to 1 (why zero)?
- What is the intuition for size of sigma relationship with bias and variance?

**SVM RESOURCES**
* http://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_ml/py_svm/py_svm_basics/py_svm_basics.html#svm-understanding
* RESOURCES 2
* http://blog.davidkaleko.com/svm-email-filter-implementation.html