---
layout: post
title: Intro to Machine Learning Week 2
---

Week 2 covers materials on multivariate linear regressions and a tutorial on Octave and Matlab. Having done some estimation and simulations of macroeconomic models during my PhD, I was already familiar with some of Matlab's syntax and so was able to skip this part. Multivariate linear regression is also a familiar topic. The new ideas here expand on the same idea from week 1, which is using the gradient descent algorithm to estimate linear equations. Some of the new and useful ideas covered are as follows:

**1\.** Much like in week 1, the multivariate linear regression is estimated using the gradient descent. This is done using the following update rule: 

<a href="{{site.url}}/img/wk2_1.png">
<img src="{{site.url}}/img/wk2_1.png" width="225" height="250"/>
</a>

This is based on the derivative of the cost function (defined as the average sum of the squared residuals).

**2\.** I was initially puzzled by the gradient descent algorithm given that an analytical solution exists for each parameter in the linear regression model. In machine learning, this is called the normal equations approach. This is done by taking the derivative of the cost function with respect to each parameter and solving for the parameter. It is then a relatively simple problem of inverting the resulting X'X matrix and taking some matrix products to solve for the parameters that minimizes the cost function. The resulting solution takes the form

    theta = (X'*X)^-1 * X' y

where X is an mxn vector and y is an mx1 vector.

This is how the statistical package I use (Stata) estimates these kind of models. It made me wonder what is the advantage of gradient descent.

It turns out that in some machine learning applications, the number of features can exceed the number of observations. In other words, m could be less than n. This makes X'X non-invertible, which, in turn, makes the normal equations approach for solving the parameters impracticable. Gradient descent doesn't have this problem, which is why it is useful in machine learning.

**3\.** Another important idea is feature scaling and mean normalization. This is just some adjustments you can make to your features to help the gradient descent algorithm converge faster. Feature scaling (or rescaling) is an adjustment to restrict the range of the feature to between 0 and 1 or between -1 and 1. Mean normalization is just the standardization of the feature so that it has zero mean and unit-variance.
