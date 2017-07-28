

Week 5 covers the algorithm for training a neural network. It involves a procedure called **backpropagation** to estimate the gradients of the cost function for each parameter (also called weights). These gradients are then used in the gradient descent algorithm to find the parameters that minimizes the cost function.

EXCERPT LINE

This lecture and the corresponding exercise has been the most difficult material so far. The implementation of the backpropagation algorithm isn't so difficult, but understanding what is going on and keeping track of the various moving parts of the algorithm requires a bit of work. Andrew also skips over many of the derivation and explanation for the equations used so I had to supplement the material with explanation from other sources (see this [blog post](http://neuralnetworksanddeeplearning.com/chap2.html) for a detailed derivation of each of the main equations). One can think of the neural network classification algortihm as a generalization of the logistic regression classification algorithm (which is simply a neural network with just an input and output layer and no hidden layer).

A hurdle to using neural networks (compared with logistic regression, for example) is in the calculation of the gradient of the cost function. For a given change in a given parameter (holding all the other parameters constant), one must account for how such a change propagates throughout the entire network. The change will pass through each layer and each activation before it manifest itself in a new value of the cost function.

Note that a single layer neural network

These gradients are important for using gradient descent to find the optimal parameters.


<a href="{{site.url}}/img/wk5_1.png">
<img src="{{site.url}}/img/wk5_1.png" width="225" height="250"/>
</a>


WHY NOT???? Why can we not just take derivative of cost function right away?




The steps to training a neural network is as follows:

1. Randomly initialize parameters ()
2. Implement forward propagation to get an initial prediction of the outcome (which would be highly inaccurate)
    * This boils down to feeding each observation in the training sample into the neural network with randomly assigned parameters
3. Calculate the cost function for these initial estimates
4. Implement backpropagation to compute the partial derivatives of the cost function with respect to each parameter
    * asdasd
5. Gradient checking by comparing backprop generated gradients with slope of cost function (a numerical estimate of gradient of cost function--WHY NOT USE THIS INSTEAD OF BACKPROP ???)
6. After calculating gradients and confirming that they are reasonable, use gradient descent to find





This procedure involves forward propagation for a given set of randomly generated values for the parameters, then backward propagation to estimate the gradients, then gradient descent to learn the optimal weights for the neural network.



## backpropagation (what is the main idea?)

The basic idea for learning a neural network is as follows:
- forward propagate for each training example to calculate output layer values
- backpropagate errors to calculate gradient
-

* what is the intuiton for the delta terms? How are they related to the derivative of the cost term in the cost function?
* backprop is just an algorithm for computing the gradients. The process for estimating the weights that minimuze sum of square residual is still using gradient descent.
* what is the intuition? for backpropagation?

### Gradient checking
- checks to make sure derivative of cost function is evaluated correctly
- disable for actual learning because it is slow (learn using backpropagation)

#### Random initialization
- symmetry breaking
- when initial starting theta are all the same across all activation units and all layers, theta are symmetric
- theta = r*2*INIT_EPSILON - EPSILON ensures that the value for theta is between +ve and -ve INIT_EPSILON




QUESTION:
- [Why not just take the derivative of the cost function with respect to each weight?]Quick question: the purpose of backprop is to get the value of the derivative of the cost function with respect to each weight. Why not just jump straight to the cost function and take the derivative with respect to each weight?

Supplementary material:
*[Detailed explanation of the backpropagation algoritm](http://neuralnetworksanddeeplearning.com/chap2.html)