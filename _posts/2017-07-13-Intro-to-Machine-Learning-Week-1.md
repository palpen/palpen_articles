---
layout: post
title: Intro to Machine Learning Week 1
comments: true
---
For week 1's post, I just define some terminologies that are new to me.

<!--excerpt-->

* **Machine learning:** "the field of study that gives computers the ability to learn without being explicitly programmed". More explicitly, a computer program is said to learn from experience E with respect to some class of tasks T and some measure of performance P, IF its performance at task T (measured by P), improves with experience E.
    * Example: predicting house prices given room size. E: data on house prices and room size; T: predict house price given room size; P: mean deviation from observed house price given room size.
* **Supervised learning:** for a given input, we observe the output in our data
* **Unsupervised learning:** deals with identifying groups or clusters based on observed characteristics. We do not know the "y" variable for some given x, but we can infer it from observing x.
* **hypothesis:** a function, call it h, that gives the best prediction of y given x. h is characterized by its functional form (linear in parameters) and its parameters. The parameters are estimated using gradient descent (for now...?).
* **Cost function:** the function we minimize to find the parameters that best describe the relationship between y and x in our data. It is the mean squared deviation between observed value of y and the y given by our hypothesis (for some given values of the parameters).
* **Gradient descent:** the algorithm used to find the parameters of our hypothesis that minimize the cost function. It takes a guess of the initial values of the parameters and, using the derivatives of the cost function, points to the local optimum through a series of incremental updating of the parameters.
* **Regression vs classification problem:** regression: continuous y variable (rainfall in mm, weight in kg, house prices); classification: categorical y variable (education categories, spam/not spam, positive / negative sentiment).
