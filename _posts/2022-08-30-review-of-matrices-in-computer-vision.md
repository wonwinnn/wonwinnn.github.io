---
layout: post
title: "Review of matrices in computer vision"
comments: false
description: "Notes"
keywords: "matrix"
author: wonwinnn
---

 This post reviews some most commonly used matrices in computer vision, mainly refers to the Appendix B of Peter Corke's book[1].  In addition, I would like to recommend *No bullshit guide to linear algebra* [2] as a quick linear algebra refresher.

### Important concepts for matrices

#### Singular

The determinant of a **square matrix** *A* is denoted $$det(A)$$.  The matrix determinant is undefined for a non-square matrix [3].  

A square matrix *A* is singular if $$ det(A) = 0$$.

A singular matrix is non-invertible. A non-singular matrix is invertible.

#### Symmetric / skew-symmetric

If matrix *A* is symmetric, then $$ A^T = A $$. 

If matrix *A* is skew-symmetric, then $$ A^T = -A $$. 

A symmetric matrix and skew-symmetric matrix will always be square. 

In Peter Corke's book it is said that "...the matrix is skew-symmetric or anti-symmetric. Such a matrix has a zero diagonal, is always singular...", but this statement is imprecisely. The correct statement should be: if *A* is an  $$n \times n$$ skew-symmetric matrix, **and *n* is odd**, then *A* is singular.

#### Orthogonal

If matrix *A* is orthogonal, then $$ A^{-1} = A^T $$.  

It can be seen that an orthogonal matrix must be non-singular ($ det(A) \neq 0$) and invertible. Actually, The determinant of an orthogonal matrix is either +1 or −1.

The column vectors (and row vectors) of an orthogonal matrix must be of unit length and orthogonal to each other. This property is useful in focal length estimation [4].

#### Normal

A matrix *A* is normal if it satisfies the equation $ A^TA = AA^T $.

All symmetric, skew-symmetric and orthogonal matrices are normal matrices.

All normal matrices are diagonalizable.

#### Positive definite / semi-definite

Real symmetric matrices can be classified according to the sign of their eigenvalues $\lambda_{i}$:

$$ \lambda_{i} > 0, \forall i \quad positive \ definite$$

$$ \lambda_{i} \geq 0, \forall i \quad positive \ semi-definite$$

$$ \lambda_{i} < 0, \forall i \quad negative definite$$

$$ otherwise \quad indefinite$$

The determinant is equal to the product of the eigenvalues, thus a positive definite matrix is non-singular.

Lemma (Least Squares and Postive Semidefiniteness) : Let $ A \in \mathbb{R}^{n \times m} $ be an $ n \times m$  matrix with $ n > m $. The matrix $ B = A^TA $  is positive semidefinite. If further the columns of $A$  are linearly independent, then the matrix $B$ is positive definite [5].

Theorem (Cholesky Decomposition) : Any positive definite matrix $ B \in \mathbb{R}^{n \times n} $ can be factorized uniquely as where $ L \in \mathbb{R}^{n \times n} $ is a lower triangular matrix with positive entries on the diagonal [5].

### Applications in computer vision

#### Rotation matrix

- Orthogonal  

#### Essential matrix

- The essential matrix is **singular**, has a **rank of 2**, and has **two equal nonzero singular values and one of zero**. The essential matrix has only **5 DoF** and is completely defined by 3 rotational and 2 translational parameters [1]. The magnitude of translation cannot be recovered due to the scale ambiguity.

#### Fundamental matrix

- Singular, rank of 2, 7 DoF

#### Homography matrix

- Non-singular, rank of 3, 8 DoF

#### Covariance matrix / fisher information matrix

- Symmetric, positive semi-definite
- Under certain standard assumptions, the Fisher information matrix is the inverse of the covariance matrix [6].

### References


[1] Corke, P. (2017). *Robotics, Vision and Control : Fundamental Algorithms In MATLAB® Second, Completely Revised, Extended And Updated Edition*. Cham: Springer International Publishing.

[2] Savov, I. (2017). *No bullshit guide to linear algebra*. Montréal, Québec: Minireference Co.

[3] Ii, R. (n.d.). *A Brief Review of Matrices and Linear Algebra*. [online] Available at:  https://www.ohio.edu/mechanical-faculty/williams/html/PDF/MatricesLinearAlgebra.pdf [Accessed 30 Aug. 2022].

[4] Benosman, R. and Kang, S.B. (2001). *Panoramic vision : sensors, theory, and applications*. New York: Springer.

‌[5] Roch, S. (n.d.). *TOPIC 1 Least squares: Cholesky, QR and Householder 3 Overdetermined systems, positive semidefinite matrices and Cholesky decomposition 3.1 Solving  an overdetermined linear system*. [online] Available at: https://people.math.wisc.edu/~roch/mmids/qr-3-overdetermined.pdf [Accessed 30 Aug. 2022].

[6] Wittman, D. (n.d.). *Fisher Matrix for Beginners*. [online] Available at: https://wittman.physics.ucdavis.edu/Fisher-matrix-guide.pdf [Accessed 30 Aug. 2022].

‌

‌
