---
title: Note | Normal Equation
date: 2021-04-01 23:54:22
mathjax: true
tags:
- Machine-Learning
- Normal-Equation
categories:
- Machine-Learning-Notes
- Notes
ShowToc: true
---

## Overview

Normal Equation is a method in parallel with gradient descent algorithm to minimize the cost function J.
<!--more-->

Differ from the gradient descent, normal equation does not need  iterate calculation, but directly calculate the stagnation points of the cost function. Since this is an analytical solution, it also has some  limits. Below is a comparison between these two methods:

|           Gradient Descent            |           Normal Equation           |
| :-----------------------------------: | :---------------------------------: |
| Need to choose learning rate $\alpha$ |            Does not need            |
|          Multiple iteration           |        One time calculation         |
|      Works well when n is large       |       Slow if n is very large       |
|     Suits for all kinds of models     | Only suitable for linear regression |



## Method

Say the dataset has *m* examples, each example contains *n* features:

Put all features into a *“m x (n+1)”* matrix, (one more column for $x_0$, always =1 )
$$
X=\begin{bmatrix}1&x^{(1)}_1&x^{(1)}_2&\cdots&x^{(1)}_n\\\vdots&\vdots&\vdots&\ddots&\vdots\\1&x_1^{(m)}&x_2^{(m)}&\cdots&x_n^{(m)}\end{bmatrix}
$$
where the cost function J is:
$$
J(\theta)=\frac{1}{2m}\sum_{i=1}^m(h_\theta(x^i)-y_i)^2
$$

$$
= \frac{1}{2m}\sum_{i=1}^m(\theta^Tx_i-y_i)^2 \href{https://duanwenbo.github.io/2021/04/01/ML-Learning-Note---polynomial-regression-and-feature-scaling/#more}{\ previous\ derive}
$$

$$
= \frac{1}{2m}(X\theta-Y)^T(X\theta-Y)\href{https://blog.csdn.net/melon__/article/details/80589759}{\ further\ derive}
$$

To find the converge solution, let:
$$
\nabla_{\theta}J(\theta)=0
$$
Hence, the solution is:
$$
\theta=(X^TX)^{-1}X^TY
$$

## Non-invertible ?

Since we used the  transform matrix of X, what if the matrix is non-invertible? Below are  two conditions in normal equation that may cause the non-invertibility.

- When it appears two linear correlation features, like meter and inch.

  Solution: Reduce one.

- When the number of features is greater than the number of examples

  Solution:  increase the datasets or decrease the considered features.

