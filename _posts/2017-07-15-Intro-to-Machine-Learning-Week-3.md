---
layout: post
title: Intro to Machine Learning Week 3
---

Week 3 covers two topics: binary classification using logistic regression and regularization (a technique that helps with addressing the problem of overfitting the data). I discuss them separately below.

## Logistic regression

It's possible to fit a linear regression model where the outcome variable is a binary (e.g. spam or not spam, malignan tumor or benign, sick or healthy). But you may not want to do this because of a couple of drawbacks. First, the fitted hypothesis resulting from the estimation of the linear regression model can give predictions that exceeds 1 or is less than zero for some values of the features. When the interpretation of the hypothesis is that it is the probability of a positive classification (say y=1 is a spam), a predicted value greater than 1 or less than zero is a little strange. But perhaps this isn't such a big deal if we, for example, make our cutoff at some value between 0 and 1 (in which case, h(theta) > 1 can be classified as a positive class).

The second drawback of the linear regression model, which makes using logistic regression more compelling for this type of problem, is it is sensitive to outliers.

<a href="{{site.url}}/img/wk3_1.png">
<img src="{{site.url}}/img/wk3_1.png" width="225" height="250"/>
</a>

At the cutoff of .5 in the figure above with the outlier observation in the far right present, the resulting decision boundary will mis-classify some of the tumors.

The logistic regression addresses

## Regularization




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
