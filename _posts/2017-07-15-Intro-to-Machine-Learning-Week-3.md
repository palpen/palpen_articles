---
layout: post
title: Intro to Machine Learning Week 3
---

Week 3 covers two topics: binary classification using logistic regression and regularization (a technique that helps with addressing the problem of overfitting the data). I discuss them separately below.

<!--excerpt-->

## Logistic regression

Here I am going to talk about the main advantages of logistic regression over linear regression when dealing with binary classification problems.

It's possible to fit a linear regression model where the outcome variable is a binary (e.g. spam or not spam, malignant tumor or benign, sick or healthy). But you may not want to do this because of a couple of drawbacks. First, the fitted hypothesis resulting from the estimation of the linear regression model can give predictions that exceeds 1 or less than zero for some values of the features. This doesn't make sense if we are interpreting the hypothesis as the probability of a positive classification (say y=1 is a spam). But perhaps this isn't such a big deal if we, for example, make our cutoff at some value between 0 and 1 (in which case, h(theta) > 1 can be classified as a positive class).

The second drawback of the linear regression model, which makes using logistic regression more compelling for binary classification problems, is its sensitivity to outliers.

<a href="{{site.url}}/img/wk3_1.png">
<img src="{{site.url}}/img/wk3_1.png" width="350" height="250"/>
</a>

At the 0.5 cutoff in the figure above, the resulting decision boundary will mis-classify tumors that are malignant as benign.

The logistic regression gets around these issues by using what is called the sigmoid function (also called the logistic function) for the hypothesis. The sigmoid function has a domain ranging from negative to positive infinity. Its range, however, is only between 0 and 1. Thus, predictions can no longer be outside of the set [0,1].

In terms of the outliers, logistic regression fits an S curve. Thus, outliers way off to the right will not significantly influence the location of the curve [Link to a figure showing this](https://www.quora.com/Can-Logistic-Regression-be-considered-robust-to-outliers). Outliers to the left, however, could still be a problem (e.g. small tumors that happen to be malignant).

One neat thing about logistic regression is the figure you can create in the 2-dimensional feature space with the line separating the positive and negative classifications. This line is called the *decision boundary*. The line is from the equation of the argument of the hypothesis, which in the simple example is a linear equation. To draw the decision boundary, set the hypothesis argument equal to the domain value of the hypothesis corresponding to the threshold (beyond which we classify a given feature as positive).

Decision boundaries need not be linear. This happens when theta'*X contain higher order polynomials.

## Regularization

*Overfitting* refers to the problem of modeling the data too precisely resulting in poor prediction when using new examples. A model that overfits exhibits *high variance*. This is because for close but different values of x, a model that suffers from overfitting will give more variation in the corresponding values of y. Conversely, it is also possible to underfit your data. A model that underfits exhibits *high bias*. The goal is to develop a model that minimizes bias and variance and strikes a happy medium maximizing prediction accuracy outside of the training sample.

Regularization is one approach used to reduce overfitting. It basically adds a term in the cost function for each parameter multiplied by a constant that is exogenously given (lambda). This constant controls the degree by which the parameters are limited in magnitude.

Regularization is not the only way to address overfitting. One can also manually select which features to keep. Later in the course, an algorithm will be taught that helps with feature selection.

I guess a way to diagnose whether your model suffers from overfitting is by testing its accuracy in predicting outcomes in your test sample (which has been set aside from the training sample). Adjustments are then made to the lambda to maximize prediction accuracy.

### Some other useful notes

Matlab function that creates the polynomial terms (nth degree) of the features X1 and X2 (e.g. X1, X2, X1.^2, X2.^2, X1*X2, X1*X2.^2, etc..):

    function out = mapFeature(X1, X2, n)
        degree = n;
        out = ones(size(X1(:,1)));
        for i = 1:degree
            for j = 0:i
                out(:, end+1) = (X1.^(i-j)).*(X2.^j);
            end
        end
    end
