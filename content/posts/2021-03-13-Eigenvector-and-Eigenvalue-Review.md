---
title: Note | Eigenvector and Eigenvalue Review 
date: 2021-03-13 23:30:31
mathjax: true
categories:
- Linear-Algebra
tags:
- Eigenvector 
ShowToc: true
---

## Basic Method
When learning the eigenvalue and eigenvector, we are commonly given an equation at the beginning
$$
AX = \lambda X \tag{1}
$$
Where
- A is the matrix
- X is the eigenvector
- $\lambda$ is the eigenvalue

### Take an example
*Q: Find the eigenvalues and eigenvectors of the matrix*
$$
A = \begin{bmatrix}
1&1&-2\\
-1&2&1\\
0&1&-1
\end{bmatrix}
$$
A: To get the answer, firstly apply the equation (1) :
$$
AX = \lambda X \tag{1}
$$

Before solving the equation, there might be something awkward, since on the right-hand side of the equation, it’s matrix-vector multiplication; while on the left-hand side, it’s the scalar-vector multiplication. 

We can rewrite the right-hand side as some kind of matrix-scalar multiplication, namely, using the identity matrix which has the effect of scaling any vector by $\lambda$

*I* is the **identity matrix** here, form like:

Hence:
$$
(\lambda I-A)X=0 \tag{2}
$$
In order to get a non-trivial solution, we get :
$$
\left| \lambda I-A\right| = 0 \tag{3}
$$
where equation (3) is also called **characteristic function**.
Expanding equation (3):
$$
\begin{bmatrix}\lambda -1&-1&2\\1&\lambda -2&-1\\0&-1&\lambda +1\end{bmatrix} = det(\lambda I -A)=\lambda^3 -2\lambda^2 -\lambda +2=0 \tag{4}
$$
Solving equation(4) we got eigenvalues as:
$$
\begin{cases}\lambda_1 = 2\\ \lambda_2 = 1\\ \lambda_3 = -1\end{cases}
$$
Now we can find the related eigenvector respectively by taking eigenvalues back to equation (2):
$$
\begin{bmatrix}1-2&1&-2\\-1&2-2&1\\0&1&-1-2\end{bmatrix}\begin{bmatrix}e_1\\e_2\\e_3\end{bmatrix}=0\ (when\ \lambda=2)
$$
hence:
$$
\frac{e_1}{-1}=\frac{-e_2}{3}=\frac{e_3}{-1}
$$
Unless otherwise stated, the eigenvectors will always be presented in their ‘simplest’ form, so the matrix of the eigenvector can be written as:
$$
\begin{bmatrix}1\\3\\1\end{bmatrix}\ (when\ \lambda =2)
$$
The other two eigenvector can be calculated similarly.

## What does it mean?
### Start from definition
looking back to the equation (1) again:
$$
AX=\lambda X \tag{1}
$$
- On the right hand side, A is a matrix, stands for a kind of linear transformation (rotation, stretching).
- On the left hand side, $\lambda$ is a scalar
- Matrix A multiply by x means applying a transformation on the vector X (rotation or stretching), and the effect of this kind of transformation is equal to the scalar $\lambda$ multiply by the vector X. (Only stretched)
- By finding the eigenvalue and eigenvector, we can find out which vectors (eigenvectors) can be stretched only by the matrix, and what’s the extent to which it’s stretched (eigenvalue.)