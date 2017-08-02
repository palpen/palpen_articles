
Week 6 covers some practical advice for how to evaluate ones model. It also talks about machine learning system design, which covers some the metrics used to evaluate the accuracy of ones model and some approaches to improve it.


## Practical machine learning advice

### Evaluating a learning algorithm
* Evaluating hypothesis
* Model selection
- intuition for a separate cross validation dataset and test datasets

### Bias vs Variance

* diagnosing bias vs variance

* if cv error and training error are about the same,
* note that the training error should decrease with high degree polynomial (as fit increases)
* high cost in test error that is close to the training error
* wheneve test cost is higher than train cost for a large enough training example. It is probably suffering from high variance. Why? High variance imply good training sample perofmrnace (low error) but bad out of sample performance (high test error).

* regularization and bias-variance

* learning curves (relates error to training sample size):
    * diagnose high bias: If your hypothesis is too simple, you can keep increasing your training sample with very litle change in the cross validation and training error. With more data, the real relationship is between y and x becomes more clear. But your hypothesis isn't changing and it continues to just fit a straight line. So increasing sample size wont change cross-validation error much (in asymptotically converges)
    * diagnose high variance: Large gap between cross-validation error and training error indicates a high variance problem, but gap decreases with more training sample. (Why?) The hypothesis isn't changing.

* Deciding what to do next
    * Trained a hypothesis that resulted in large error out of sample. What can you do?
    * first identify if high variance or high bias

* fixing high variance problem:
    *


## Machine learning system design

### error analysis
* Start with a simple algorithm and implement it quickly (within a day if possible). Avoid pre-mature optimization
* Look at the cases where the algorithm is missclassifying. Can you identify if there is anything in common across these missclasifeied training examples?
* Have a numerical evaluation of learning algorithm. Calculate single number that tells you how well your algorithm is doing. Look at cross-validation error with stemming vs withut stemming, for example. Basically, whenever you make changes to your features or the way you process the data, you use the cross validation error to evaluate your algorithm. Just use the cross validation error when trying new ideas.
    * 

### Handling skewed classes
Skewed data are cases where the positive classes are much smaller than the negative classes. In the example in the course, you might have data on cancer diagnoses. The data may be skewed because typically in a given sample, you will only have a few observation who were classified as having cancer and a much larger number of observation who do not have cancer. 

This may be problematic for the following reason: suppose you train your algorithm and evaluate it on your test case and find that it was able to diagnose 99% of the cases correctly. Error is only 1%. But suppose only 0.5% of the patients in the test sample actually have cancer. An function that always classifies every case as no-cancer will only be wrong for 0.5% of the cases (i.e. those who actually have cancer). Thus, one must be careful when dealing with skewed classification.

The metrics used for evaluating data with skewed classes are the following:

>  **Precision:** Of all patients we predicted as having cancer, what fraction actually have cancer? Defined as Number of true positives / Number predicted as positive
>   **Recall:** Of all patients that actually have cancer, what fraction did we correctly predict to have cancer? Defined as Number of true positives / number of actual positives


  
INSERT Predicted and ACtual TABLE HERE (SEE SCREEN SHOT)


Given these two metrics, a function that always predicts no cancer will have undefined precision (0/0) and zero recall. Thus, it cannot possibly pass for a good algorithm even if it happens to lower the cross-validation error.

There is, however, a trade off between these two metrics. Because of the way they are defined, increasing precision decreases recall and increasing recall decreases  precision. For example, classifying every sample as having cancer captures every person who actually has cancer, but the increase in the number of those predicted positive decreases precision.

The metric that accounts for both preceision and recall is the [F1-Score](https://en.wikipedia.org/wiki/F1_score). The goal is tune ones learning algorithm in a way that to maximizes this value.

#### Trading off precision and learning



### Large data sets