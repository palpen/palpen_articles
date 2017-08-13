
# Support vector machines (SVM)

Week 7 covers the support vector machine (SVM) algorithm. This is the last supervised learning algorithm in the course.

EXCERPT

There are many good resources for learning explaining how the support vector machine (SVM) algorithm works. The best one is certainly the material covered in the Coursera course. I suggest you check it out. But here are some other resources that also explain it fairly well:

**SVM RESOURCES**
* http://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_ml/py_svm/py_svm_basics/py_svm_basics.html#svm-understanding

SVMs is hailed to be a very powerful learning algorithm for non-linear classification. In its basic form, the algorithm looks for the line that most "cleanly" separates the different classifications in the data. By cleanly, it finds the line with the largest margin on either side. This is why the SVM is sometimes also called a **large margin classifier**.

Consider the example below

<a href="{{site.url}}/img/wk7_8.png">
<img src="{{site.url}}/img/wk7_8.png" width="350" height="150"/>
</a>

In the figure above, the line the most *cleanly* separates the classes X from O is the negatively sloped line running between the two classes. The two nearly vertical line also separates the two classes, but they are not the decision boundary that is optimal.

There are some similarities between logistic regression and SVMs. For one, 



The underlying mechanics of finding this decision boundary is fairly involved. 




What is the major advantage of SVM over other learning algorithms?

$$MATH$$
$$\sum_{n}^{i=1}$$

## Large Margin Classification

## Kernel 1

## Kernel 2

## SVMs in Practice

#### advantages

#### disadvantages



### Questions:
- Why is the hypothesis equal to 1 when theta * X is greater than zero? (first video)? Why isn't it greater than or equal to 1 (why zero)?
- What is the intuition for size of sigma relationship with bias and variance?


### to add to blog post: 
* find one or two additional references for SVM (in addition to Coursera)

 Logis(c regression vs. SVMs
number of features ( ),   number of training examples If   is large (rela2ve to ):
Use logis2c regression, or SVM without a kernel (“linear kernel”)
If   is small,   is intermediate: Use SVM with Gaussian kernel
If   is small,   is large:
Create/add more features, then use logis2c regression or SVM without a kernel
Neural network likely to work well for most of these secngs, but may be slower to train.