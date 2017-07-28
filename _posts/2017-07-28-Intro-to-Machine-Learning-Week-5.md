---
layout: post
title: Intro to Machine Learning Week 5
comments: true
---

Week 5 covers the algorithm for training a neural network. It involves a procedure called **Backpropagation** to estimate the gradients of the cost function for each parameter (also called weights). These gradients are then used in the gradient descent algorithm to find the parameters that minimizes the cost function.

<!--excerpt-->

This lecture and the corresponding exercise has been the most difficult material so far. The implementation of the backpropagation algorithm isn't so difficult, but understanding what is going on and keeping track of the various moving parts of the algorithm requires a bit of work. Andrew Ng also skips over many of the derivation and explanation for the equations used, which led me to seeking for supplementary materials from outside sources (see this [blog post](http://neuralnetworksanddeeplearning.com/chap2.html) for a detailed derivation of each of the main equations). I found it useful to think of the neural networks algortihm as a generalization of the logistic regression algorithm (which is simply a neural network with just an input and output layer).

A hurdle to using neural networks (compared with logistic regression, for example) is in the calculation of the gradient of the cost function. It is much more complicated than in the logistic regression case because of the multiple interdependent layers through which a change in the parameter must pass through. For a given change in a given parameter (holding all the other parameters constant), one must account for how such a change propagates throughout the entire network. The change must pass through each layer and each activation unit before it manifest itself in a new value of the cost function. It turns out that there's a single formula that captures this:

<a href="{{site.url}}/img/wk5_1.png">
<img src="{{site.url}}/img/wk5_1.png" width="350" height="150"/>
</a>

The **delta** terms are the "error" terms defined as the derivative of the cost function with respect to the weighted sum of the activation units in a given layer (denoted by z). The **a** terms is the jth activation unit for that layer.

Once the gradients of the cost function has been calculated, the gradient descent algorithm can then be used to find the optimal parameters.

Here is a summary of the algorithm to train a neural network:

**1.** Randomly initialize each parameter (cannot set them all to be the same to ensure symmetry breaking)

**2.** Implement forward propagation to get an initial prediction of the outcome (which will have high error)
    * This boils down to feeding each observation in the training sample into the neural network with the randomly assigned parameters

**3.** Calculate the cost function using these initial predictions

**4.** Implement backpropagation to compute the partial derivatives of the cost function with respect to each parameter
    * This is using the formula above

**5.** Apply gradient checking by comparing gradients estimated in 4\. with slope of cost function (we can estimate the gradient using these slope estimates in place of backpropagation, but it is very slow). Disable gradient checking when actually training the network.

**6.** After calculating gradients using backpropagation (and confirming that they are reasonable), use gradient descent to find the optimal parameters that minimizes the cost function.

