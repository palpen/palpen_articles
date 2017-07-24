---
layout: post
title: The meaning of overfitting and why underfitting imply high bias
comments: true
---

Here's an excerpt to a very clear definition of what it means for your statistical model to suffer from overfitting [(original post)](http://andrewgelman.com/2017/07/15/what-is-overfitting-exactly/):

<!--excerpt-->

> If your model is correct, “overfitting” is impossible. In its usual form, “overfitting” comes from using too weak of a prior distribution.

> ...

> One way to define overfitting is when you have a complicated statistical procedure that gives worse predictions, on average, than a simpler procedure.

> ...overfitting can happen. And it happens when the larger model has too weak a prior. After all, the smaller model can be viewed as a version of the larger model, just with a very strong prior that restricts some parameters to be exactly zero.

I like the last point in the post because it ties into why models that are too simple are described to exhibit high bias (and, hence, suffers from underfitting).
