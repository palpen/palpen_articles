

### Evaluating a learning algorithm
- intuition for a separate cross validation dataset and test datasets

### Bias vs Variance and cost functions
* if cv error and training error are about the same,
* note that the training error should decrease with high degree polynomial (as fit increases)
* high cost in test error that is close to the training error
* wheneve test cost is higher than train cost for a large enough training example. It is probably suffering from high variance. Why? High variance imply good training sample perofmrnace (low error) but bad out of sample performance (high test error).

* learning curves (relates error to training sample size):
    * diagnose high bias: If your hypothesis is too simple, you can keep increasing your training sample with very litle change in the cross validation and training error. With more data, the real relationship is between y and x becomes more clear. But your hypothesis isn't changing and it continues to just fit a straight line. So increasing sample size wont change cross-validation error much (in asymptotically converges)
    * diagnose high variance: Large gap between cross-validation error and training error indicates a high variance problem, but gap decreases with more training sample. (Why?) The hypothesis isn't changing.

* Deciding what to do next
    * Trained a hypothesis that resulted in large error out of sample. What can you do?
    * first identify if high variance or high bias

* fixing high variance problem:
    *