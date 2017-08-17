---
layout: post
title: Intro to Machine Learning Week 6
comments: true
---

Week 6 covers some approaches that you can use to evaluate the performance of your model. These includes the trade-off between bias and variance and how to diagnose which is present by comparing the various error metrics calculated using the training, cross-validation, and test dataset. It also talks about some approaches for evaluating error cases in the algorithm, issues arising from classification problems with skewed classes, and scenarios under which large datasets can be useful.

<!--excerpt-->

## Practical machine learning advice

### Evaluating a learning algorithm

This lecture takes a break from learning new algorithms and talks about some of the practical guidelines to practicing machine learning. Andrew introduces the importance of using different datasets for training your algorithm and estimating its parameters and for evaluating its performance. In particular, your dataset should be split into three sets: a **training set**, a **cross-validation set**, and a **test set**. The recommended split is 60 / 20 / 20. The reason for splitting them is because the training set is used to estimate the parameters of the learning algorithm. Given that the gradient descent algorithm chooses the parameters that minimizes the cost function, the cost calculated using the training set will always be lower than the cost calculated using any other dataset. Your learning algorithm may achieve very low error in the training dataset but have high error out of sample.

The purpose of the training set is solely for estimating the parameters of your learning algorithm. The cross-validation set is for other adjustments to your model that can improve its performance. These include changing the number of the polynomial degree of your hypothesis, changing the value of the regularization parameters, or changes to the size of the training set. The test set is the final test after the training of the learning algorithm *and* each of the subsequent adjustments mentioned previously have been optimized.

Here are the steps for how to choose the best polynomial degree to fit the data and the role that each dataset play in this process:

1. Optimize the parameters using the training set for each polynomial degree, d.
2. Find the polynomial degree d with the least error using the cross-validation set.
3. Estimate the generalization error using the test set with the degree of the polynomial that minimized the cross-validation error.

### Bias vs Variance

Recall that a model with high bias suffers from underfitting and a model with high variance suffers from overfitting. Both contributes to high out-of-sample error. The goal is to find the function that minimizes bias and variance to maximize out-of-sample accuracy of your learning algorithm.

#### Bias vs Variance and degree of polynomial

The trade-off between bias and variance as we increase the degree of the polynomial is summarized in the following figure:

<a href="{{site.url}}/img/wk6_2.png">
<img src="{{site.url}}/img/wk6_2.png" width="375" height="350"/>
</a>

As the degree of the polynomial increases, training error decreases. This is heading towards overfitting territory. To determine the point where we have overfit, we compare this with the cross-validation error. If the gap is large, then our model is suffering from overfitting and we should decrease the degree of the polynomial. But, decreasing it by too much may result in underfitting. This is where both training and cross-validation error is high and similar in value.

#### Bias vs Variance and regularization

We can also the address bias and variance trade-off by adjusting our regularization parameter, lambda. The regularization parameter penalizes model parameters (the thetas) that are too high.

The figure relating the value of the regularization parameter, lambda, to the cost functions calculated using the training set and the cross-validation set is below. 

<a href="{{site.url}}/img/wk6_1.png">
<img src="{{site.url}}/img/wk6_1.png" width="375" height="350"/>
</a>

As lambda increases, we penalize the parameters for being too high, increasing the likelihood of underfitting. This monotonically increases training error because we started with a slightly overfitted model (when lambda was low) but now ended with a simpler model that is a poorer approximation of the data.

The cross-validation error starts out high because with low lambda, the model overfits the training data. It decreases with larger lambda up until lambda is too large and the the model now suffers from underfitting, thereby increasing the cross-validation error.


Here are the explicit steps from the course to undertake this experiment:

1. Create a list of lambdas (i.e. λ∈{0,0.01,0.02,0.04,0.08,0.16,0.32,0.64,1.28,2.56,5.12,10.24})

2. Create a set of models with different degrees or any other variants.

3. Iterate through the λs and for each λ go through all the models to learn some Θ.

4. Compute the cross-validation error using the learned Θ (computed with λ) on the cross-validation dataset without regularization or λ = 0.

5. Select the best combo that produces the lowest error on the cross-validation set.

6. Using the best combo Θ and λ, apply it to the cost function using the test dataset to see if it has a good generalization of the problem.

It is important to note that when calculating the cross-validation error, we must use the unregularized cost function (lambda = 0). In this case, we just want the true error to evaluate the model using the estimated parameters.

#### Bias vs Variance and training set size

This part relates the bias and variance trade-off to the size of training set (i.e the sample size). Getting more data is not always a panacea. It is only useful in the case where the model suffers from high variance (overfitting). Why? consider the following example. Suppose the true data generating function is a cubic. If we fit a straight line through the data, our model will suffer from high bias. Even if we had more data, we have not changed the functional form of our hypothesis and the data generating process continues to be a cubic. Thus, with greater data we still have an underfitting problem if we do not change the functional form of our hypothesis.

In the high bias case, plotting the training error and the cross-validation error against increasing sample size will result in the two curves converging at some constant high error value.

It is only in the high variance case where more training data can help. Here, the cross-validation error decreases as the sample size increases. Training error, on the other hand, increases with sample size. This is because the fit becomes less perfect with more data points (assuming the degree of the polynomial is sufficiently high).

#### Summary of the various fixes to address high bias and high variance

This was taken verbatim from the course notes:

> * **Getting more training examples:** Fixes high variance
> * **Trying smaller sets of features:** Fixes high variance
> * **Adding features:** Fixes high bias
> * **Adding polynomial features:** Fixes high bias
> * **Decreasing λ:** Fixes high bias
> * **Increasing λ:** Fixes high variance.


## Machine learning system design

### Error analysis

In this part of the lecture, Andrew Ng offers some guidelines for how to deal with cases where your algorithm failed to correctly classify an example.

* Start with a simple algorithm and implement it quickly (within a day if possible). Avoid premature optimization.
* Manually go through the cases where the algorithm is misclassifying examples. Can you identify if there is anything in common across these misclassified training examples?
* Have a numerical evaluation of the learning algorithm. Calculate single number that tells you how well your algorithm is doing. In natural language processing projects, for example, look at cross-validation error with [stemming vs without stemming](https://en.wikipedia.org/wiki/Stemming) of words. In summary, whenever you make changes to your features or the way you process the data, you use the cross-validation error to evaluate your algorithm. Then, once you have achieved a low enough cross-validation error, use the test dataset to evaluate your estimated hypothesis using the adjustments you made. The error calculated using the test dataset should never be used to guide the adjustments to the various parameters of the algorithm (e.g. regularization parameter). It should also never be used to guide the way you process the data or create features to include in the learning algorithm.

### Handling skewed classes
Data that have skewed classifications are cases where the positive classes are much smaller than the negative classes. Consider cancer diagnoses (the example given in the course). The data may be skewed because typically in a given sample, you will only have a few observation who were classified as having cancer and a much larger number of observation who do not have cancer.

This may be problematic for the following reason: suppose you train your algorithm and evaluate it on your test case and find that it was able to diagnose 99% of the cases correctly. Error is only 1%. But suppose only 0.5% of the patients in the test sample actually have cancer. An function that always classifies every case as no-cancer will only be wrong for 0.5% of the cases (i.e. those who actually have cancer). This appears to be an improvement on the previous hypothesis but it would gravely suffer making predictions in the test data. One must be careful when dealing with skewed classification.

The metrics used for evaluating data with skewed classes are the following:

>  **Precision:** Of all patients we predicted as having cancer, what fraction actually have cancer? Defined as Number of true positives / Number predicted as positive

>   **Recall:** Of all patients that actually have cancer, what fraction did we correctly predict to have cancer? Defined as Number of true positives / number of actual positives

<a href="{{site.url}}/img/wk6_3.png">
<img src="{{site.url}}/img/wk6_3.png" width="400" height="350"/>
</a>

Given these two metrics, a function that always predicts no cancer will have undefined precision (0/0) and zero recall. Thus, it cannot possibly pass for a good algorithm even if it happens to lower the cross-validation error.

There is, however, a trade off between these two metrics. Because of the way they are defined, increasing precision decreases recall and increasing recall decreases  precision. For example, classifying every sample as having cancer captures every person who actually has cancer, but the increase in the number of those predicted positive decreases precision.

The metric that accounts for both precision and recall is the [F1-Score](https://en.wikipedia.org/wiki/F1_score). The goal is tune your learning algorithm in a way that maximizes this value.

### Large data sets

Finally, Andrew touches on when it is useful to use a large dataset. A large dataset is only useful if the features in it is sufficient to predict y. A dataset containing house prices and just one feature for number of rooms will not be useful even if you have a million observations.

A simple test is to ask yourself "given the features in this dataset, can a human expert in this domain give a reasonably accurate prediction of y?" If yes, then having more observations in your training dataset can be useful. To make the large dataset even more effective, use a learning algorithm with many parameters (such as a logistic regression with many features or a neural network with many hidden units). This ensures that your learning algorithm doesn't suffer from high bias where in which case a large dataset would be useless.
