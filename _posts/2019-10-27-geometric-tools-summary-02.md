---
title: "Square Matrix"
categories:
  - Computer Graphics
tags:
  - Linear Algebra
d3: true
MathJax: true
---

## Diagonal Matrices
k, k의 항을 제외한 나머지가 모두 0인 matrix.  
사선 방향으로 항이 위치한다.

$$
M = 
\begin{bmatrix}
a_{1,1} & 0       & \dots  & 0       \\
0       & a_{2,2} & \dots  & 0       \\
\vdots  & \vdots  & \ddots & \vdots  \\
0       & 0       & \dots  & a_{n,n} \\
\end{bmatrix}
$$

### Diagonal matrix 특성
1. $A, B$가 diagonal이면, $C = AB$도 diagonal. 또한 전체 항을 곱할 필요 없이 $c_{k,k} = a_{k, k}b_{k, k}$ 로 구할 수 있다.
2. $A, B$가 diagonal이면, 교환 법칙이 성립한다. $C = AB = BA$
3. $A$는 diagonal, $B$는 일반 matrix면 $C = AB$에서 $k$번째 행은 $B$의 $k$번째 행을 $a_{k,k}$로 곱한 결과이다. $C = BA$ 일때는 $B$의 $k$번째 열을 $a_{k,k}$로 곱한 결과이다.

### Scalar Matrices
모든 항이 같은 diagonal matrix

$$
M = 
\begin{bmatrix}
\alpha & 0      & \dots  & 0      \\
0      & \alpha & \dots  & 0      \\
\vdots & \vdots & \ddots & \vdots \\
0      & 0      & \dots  & \alpha \\
\end{bmatrix}
$$

### Identity Matrices
Dialgonal matrix 중 모든 항이 1인 matrix로, matrix의 곱셈 연산에서의 항등원 matrix $I$ ($IM = MI = M$)  

$$
I_{n} = 
\begin{bmatrix}
1      & 0      & \dots  & 0      \\
0      & 1      & \dots  & 0      \\
\vdots & \vdots & \ddots & \vdots \\
0      & 1      & \dots  & 0
\end{bmatrix}
$$

## Triangular Matrices
삼각형 꼴의 matrix로, *upper triangluar*, *lower triangular* matrix로 나뉜다.

$$
M_{upper} = 
\begin{bmatrix}
a_{1,1} & a_{1,2} & \dots  & a_{1,n} \\
0       & a_{2,2} & \dots  & a_{2,n} \\
\vdots  & \vdots  & \ddots & \vdots  \\
0       & 0       & \dots  & a_{n,n}
\end{bmatrix}
$$

### Triangular matrix의 특성
1. $A, B$가 lower triangular이면 $C = AB$도 lower triangular matrix이다(upper도 마찬가지).
2. $A, B$가 lower triangular이면 $C = A + B$도 lower triangular matrix이다(upper도 마찬가지).
3. $A$가 invertible한 (역행렬을 취할 수 있는) lower triangular matrix면 $A^{-1}$도 lower triangular이다(upper도 마찬가지).

## Determinant

### Determinant 계산


### Determinant의 특성


## Inverse

### Inverse의 특성


### Inverse가 존재하는 조건


### Singular Matrix


