---
title: "Break into Machine Learning for Economic and Statistical Students"
date: 2019-05-13T22:35:53+02:00
draft: false
tags: ["Machine Learning", "Economics", "Statistics", "Python"]
---

<div style="text-align:justify">

With the rise of artificial intelligence, knowing how to programme is quite essential for most students how are doing science degree. We are seeing that more and more students from economic department are enrolled in the Machine Learning course world widely. Meanwhile, trained future statisticians are exploring to become a professional data scientist. However, both economic students and statistic students might have very mixed feeling on Machine Learning Modules. On one hand, you might feel the contents from machine learning are very familiar to you. For instance, the logistic regression for classification has been covered and practiced from both econometric and statistic classes. However, on the other hand, you might be lost temporarily when you heard about gradient descent for risk optimization.

How should economic and statistic student break into Machine Learning? This blog presents some thoughts on this question. To avoid the plagiarism, I have to declare that all material used in this blog are taken from the classical course by [Andrew Ng](https://see.stanford.edu/course/cs229), unless ortherwise stated.

## Go for Broad View

To get the gist of machine learning, we need have the broad view. As a subject of AI module, machine learning is the study on training computer to learn the certain tasks by feeding the large dataset. If one method can be only used to solve problems related to time series dataset, it should not be called machine learning. Therefore, when we study machine learning, we want to have the very broad view or very general method to cover different datasets, such as cross-sectional, panel and time series dataset, ect,. *All you have studied from econometrics or statistics, like logistic models, autoregression models, are just the subsets of machine learning models*.

> Generally, we want to have the optimal statistical inference. To have the optimal inference, we need employ the optimization methods

## Set the Benchmark

To optimize is to search the algorithms for satisfying the Benchmark. In machine learning, the most common one is the **cost function** (or square error). Although we will never know the true data generate process, we can propose an function $f(x)$ (it can be linear or nonlinear) to represent it. Whether function $f(x)$ is good enough depends on how it can minimize the cost function:
$$J(\theta) = \frac{1}{2} \sum\_{i=1}^m [f\_{\theta}(x^i) - y^i]^2$$

where $y$ is the true value.

This function looks nice as even hight school student can have some sense of knowing how to solve it. No matter this cost function is in matrix format or scalar format, it is just a quadratic function. I guess any reader who ends up here knows how to find the minimum of functions like this one:
$$y = 2x^2 - 3x + 4$$

> Yes, it's all about differentiation

Now, let's differentiate the **cost function** in terms of parameters or coefficients $\theta$ by assuming the simplest case: only one training example $(x, y)$:
$$\begin{aligned}
\frac{\partial}{\partial \theta\_j} & = \frac{\partial}{\partial \theta\_j} \frac{1}{2} [f\_{\theta}(x) - y]^2 \\\\
& = 2 \cdot \frac{1}{2} [f\_{\theta}(x) - y] \frac{\partial}{\partial \theta\_j}[f\_{\theta}(x) - y] \\\\
& = [f\_{\theta}(x) - y] \cdot \frac{\partial}{\partial \theta\_j} \big ( \sum\_{i=0}^n \theta\_i x\_i \big) \\\\
& = [f\_{\theta}(x) - y] x\_j
\end{aligned}$$

Put the above result, we can have the update rule:
$$\theta\_j = \theta\_j + \alpha [y^i - f\_{\theta}(x^i)] x\_j^i$$

This rule is called **LMS** update rule, where $\alpha$ is called the **learning rate**. This rule is also knowns as **Widrow-Hofff** learning rule.
