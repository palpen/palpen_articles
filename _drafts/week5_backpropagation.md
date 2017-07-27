

Week 5 covers the algorithm for training a neural network. This procedure involves forward propagation for a given set of randomly generated values for the parameters, then backward propagation to estimate the gradients, then gradient descent to learn the optimal weights for the neural network.



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


Supplementary material:
*[Detailed explanation of the backpropagation algoritm](http://neuralnetworksanddeeplearning.com/chap2.html)