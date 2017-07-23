---
layout: post
title: Intro to Machine Learning Week 4
comments: true
---

Weeks 4 of the course introduces Neural Networks, a learning algorithm modeled after the brain. I discuss the algorithm at a very high level given that the details is quite involved. I focus instead on talking about the problem it solves, an outline of its implementation, and some issues that may arise.

<!--excerpt-->

Neural networks is useful for cases where the classification problem requires a very complicated non-linear decision boundaries to accurately make predictions. In these cases, the problem lies in modeling the hypothesis using higher order polynomials typically for very many features. For example, to predict house prices your data may include features containing information on size in sq. feet, number of bedrooms, number of floors, age, etc. In addition to these individual features, you may need to construct interaction terms of these features. This results in an increasingly complicated hypothesis equation.

The problem of modeling a decision boundary that is non-linear and containing very many features is more salient in image recognition. A black and white image, for example, is made up of individual pixels. An image is characterized by the value of each of its pixel (the value represents the intensity of the shade). A 50x50 pixel image will contain 2500 pixels and each pixel is a feature. If we were to include just the quadratic of the features (e.g. x1*x1, x1*x2, etc), the number of features explodes to 2500*(2499)/2 = 3,123,750 features. It is computationally expensive to estimate a hypothesis with this many features.

To deal with manifold and complex features, the neural networks algorithm "splits" the processing of the input features by passing them into various *activation units* organized into *layers*

<a href="{{site.url}}/img/wk4_2.png">
<img src="{{site.url}}/img/wk4_2.png" width="350" height="250"/>
</a>

The notation **a** inside each pink circle in layer 2 represents an activation unit in that layer. This example contains only one *hidden* layer. Neural networks can have many activation units and many hidden layers depending on the complexity of the classification problem. Each activation unit in a given layer is estimated using logistic regression (estimating the parameters of the sigmoid function) and ranges in value between 0 and 1.