---
layout: post
title: Intro to Machine Learning Week 7
comments: true
---

Week 7 covers the support vector machine (SVM) algorithm. This is the last supervised learning algorithm covered in the course.

<!--excerpt-->

SVMs is hailed to be a very powerful learning algorithm for non-linear classification. In its basic form, the algorithm looks for the line that most "cleanly" separates the various classifications in the data. By cleanly, it finds the line with the largest margin on either side. Because of this, the SVM algorithm is also called a **large margin classifier**.

Consider the example below:

<a href="{{site.url}}/img/wk7_8.png">
<img src="{{site.url}}/img/wk7_8.png" width="350" height="250"/>
</a>

In the figure, the line the most *cleanly* separates the Xs from the Os is the negatively sloped line running between them. The two nearly vertical line also separates the two classes, but they are not the decision boundary that is optimal.

The SVM algorithm uses a cost function that have a similar structure to the cost function of the logistic regression. In the logistic regression, the cost function includes the log of the sigmoid function and the log of 1 minus the sigmoid function. For SVM, these terms are replaced by a piecewise function that looks like the following, depending on the value of y (they are the dark blue line tracing the cost terms in the logistic regression cost function)

<a href="{{site.url}}/img/wk7_2.png">
<img src="{{site.url}}/img/wk7_2.png" width="350" height="250"/>
</a>

<a href="{{site.url}}/img/wk7_3.png">
<img src="{{site.url}}/img/wk7_3.png" width="350" height="250"/>
</a>

The structure of these terms of the cost function in SVM is what gives rise to the large margin characterization of the decision boundary.

SVMs can model very complex non-linear decision boundaries. In the logistic regression case, we can model non-linear decision boundaries by using higher-order polynomial features. The drawback of this approach is that it can become computationally expensive to train the model, especially in cases where the data has a very rich set of features. Another complicated decision boundary could be a case where you cannot split the two classes with one continuous line (see examples [here](http://haohanw.blogspot.ca/2014/03/ml-how-sigma-matters-in-svm-rbf-kernel.html)).

The SVM algorithm gets around this by using a kernel to map two data points--a training example and a landmark--to a value representing the similarity between the two. The kernel used in the course is the [Gaussian kernel](https://en.wikipedia.org/wiki/Radial_basis_function_kernel) (also called the Radial basis function kernel), but one can also try other kernels (the ones suggested in the course are the linear kernel and the polynomial kernel).

I still don't understand the math behind the kernel trick. Based on my reading of outside sources, the kernel is applied to project the data to a different feature space. This is important especially if the data is non-linearly separable. In such a case, the kernel trick in SVM allows the projection of the data into a space where it will be linearly separable. I definitely need to revisit this in the future to understand the details.

## SVM Gaussian kernel parameters, bias and variance, and feature scaling

There are two parameters to tune when using SVM with the Gaussian kernel: C and $$\sigma$$. C is just the inverse of the regularization parameters, $$\lambda$$. With greater C, $$\lambda$$ must be small. This means we are more likely to overfit (greater variance). Conversely, a small C imply a large $$\lambda$$. This makes the algorithm more likely to underfit (greater bias).

$$\sigma$$ is the Gaussian kernel parameter controlling the speed at which the value of the function changes as you move away from its peak. A smaller $$\sigma$$ results in a steeper slope around the peak. Conversely, a higher $$\sigma$$ results in a flatter kernel function.

What is the implication of this? A small $$\sigma$$ tends to overfit (high variance). This happens because when $$\sigma$$ is very small, a given example $$x^{(i)}$$ needs to be very close to the landmark for the kernel function to be non-zero. Thus, the example $$x^{(i)}$$ will only be classified as a given class if it is very close (measured using the Euclidean norm) to a landmark of that class. This is equivalent to overfitting in that any slight deviation from a given class immediately results in the hypothesis assigning a different classification (see [here](http://haohanw.blogspot.ca/2014/03/ml-how-sigma-matters-in-svm-rbf-kernel.html) for a good explanation of this with figures).

Conversely, a large $$\sigma$$ tends to underfit (high bias). In this case, the Gaussian kernel function is flat. This means that the example can be far from a given landmark and still result in the kernel being non-zero. Thus, although the example is far from the landmark, it can still be classified according to the same classification as that landmark.

Lastly, it was also advised to perform feature scaling if features have very different scales (e.g. house prices vs number of rooms). This improves performance and ensures that small scale features are not ignored.

## Logistic regression vs SVMs

SVM with the Gaussian kernel is best used in cases where there are relatively few features compared to the number of observations in the data. Also, the number of observations, m, shouldn't be too large. This is because the algorithm must estimate m+1 parameters. The guideline is n=1 to 1,000 features and m = 10 to 50,000 observations.

If m is very large (but is still greater than the number of features), using SVM becomes computationally expensive. Use logistic regression or SVM with a linear kernel instead. It was also recommended to use these methods instead of SVM with a non-linear kernel if there are more features than observations (e.g. text classification problem with many features (words), but small number of text).
