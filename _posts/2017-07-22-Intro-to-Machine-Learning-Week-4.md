---
layout: post
title: Intro to Machine Learning Week 4
comments: true
---

Weeks 4 of the course introduces Neural Networks, a learning algorithm modeled after the animal brain. I discuss the algorithm at a very high level given that the details is quite involved. I focus instead on the problem it was designed to solve.

<!--excerpt-->

Neural networks is useful for cases where the classification problem requires a very complicated non-linear decision boundary in order to make accurate predictions. In these cases, the problem lies in modeling the hypothesis using higher order polynomials typically for very many features. For example, to predict house prices, your data may include features containing information on size in sq. feet, number of bedrooms, number of floors, age, etc. In addition to these individual features, you may need to construct interaction terms of these features. This results in an increasingly complicated hypothesis equation.

The problem is more salient in image recognition. A black and white image is made up of individual pixels. An image is characterized by the value of each of its pixels (representing the intensity of the shade). A 50x50 pixel image will contain 2500 pixels where each pixel is a feature. If we were to include just the quadratic of the features (e.g. x1*x1, x1*x2, etc), the number of features explodes to 2500*(2499)/2 = 3,123,750 features. It is computationally expensive to estimate a hypothesis with this many features.

To deal with manifold and complex features, the neural networks algorithm "splits" the processing of the input features by passing them into various *activation units* organized into *layers*

<a href="{{site.url}}/img/wk4_2.png">
<img src="{{site.url}}/img/wk4_2.png" width="350" height="250"/>
</a>

The notation **a** inside each pink circle in layer 2 represents an activation unit in that layer. This example contains only one *hidden* layer. Neural networks can have many activation units and many hidden layers depending on the complexity of the classification problem. Each activation unit in a given layer is a sigmoid function and, therefore, ranges in value between 0 and 1.

Here is the mathematical representation of the simple neural network above. g(.) is the sigmoid function.

<a href="{{site.url}}/img/wk4_3.png">
<img src="{{site.url}}/img/wk4_3.png" width="350" height="250"/>
</a>

The next lecture covers the estimation of the parameters in a neural network using the *backpropagation algorithm*. It is still not clear to me what role the activation units and the different layers play in the entire process. For example, what information is being passed through in each activation function in each layer (particularly in the layers following the input layer)? How do we interpret the activation unit evaluated at some training example? is it a probability?
