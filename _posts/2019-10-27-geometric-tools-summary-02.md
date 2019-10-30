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
Square matrix에서 계산되는 값으로, det(M) 혹은 $|M|$으로 표현한다.

$$
|M| =
\begin{vmatrix}
a_{1,1} & a_{1,2} \\
a_{2,1} & a_{2,2}
\end{vmatrix}
$$

### Determinant 계산 by Laplacian expansion
계산 과정을 보기에 앞서 *submatrix*, *minor*, *cofactor*에 대한 이해가 필요하다.  
*submatrix*는 특정 행/열을 지운 결과 matrix이다.  
아래 예시는 $4\times4$ matrix $M$에서 네번째 행과 세번째 열을 지워서 만든 submatrix $M'_{4,3}$의 결과이다.

$$
M =
\begin{bmatrix}
3 & 9 & 2 & 5 \\
2 & 7 & 1 & 3 \\
8 & 4 & 6 & 1 \\
9 & 5 & 2 & 6
\end{bmatrix}

\Longrightarrow

M'_{4,3} =
\begin{bmatrix}
3 & 9 & 5 \\
2 & 7 & 3 \\
8 & 4 & 1
\end{bmatrix}
$$

*Minor*는 $a_{i,j}$항에 대한 submatrix의 determinant이다.  
$i$행, $j$ 열을 지운 submatrix $M'_{i,j}$가 대상이 된다.

$a_{i,j}$항에 대한 *cofactor* $c_{i,j}$는 해당 항에 대한 minor, 혹은 그 음수 값이다.  

$$c_{i,j} = (-1)^{i+j}|M'_{i,j}|$$

이제 $3\times3$ matrix에서 위 개념들을 활용해 cofactor를 기반으로 determinant를 구해보자.  

$$
\begin{vmatrix}
a_{1,1} & a_{1,2} & a_{1,3} \\
a_{2,1} & a_{2,2} & a_{2,3} \\
a_{3,1} & a_{3,2} & a_{3,3}
\end{vmatrix}
= a_{1,1}
\begin{vmatrix}
a_{2,2} & a_{2,3} \\
a_{3,2} & a_{3,3}
\end{vmatrix}
- a_{1,2}
\begin{vmatrix}
a_{2,1} & a_{2,3} \\
a_{3,1} & a_{3,3}
\end{vmatrix}
+ a_{1,3}
\begin{vmatrix}
a_{2,1} & a_{2,2} \\
a_{3,1} & a_{3,2}
\end{vmatrix}
$$

일반적으로 $n\times n$ matrix의 determinant는 $(n - 1) \times (n - 1)$ determinant들의 합으로 구할 수 있다.  
마찬가지로 각각의 $(n - 1) \times (n - 1)$ determinant는 같은 방법을 적용하여 구할 수 있으므로, 1개의 항으로 이루어진 matrix까지 도달하면 최종 결과를 얻을 수 있다.

### Determinant의 특성
1. $\|M\| = \|M^{T}\|$
2. $\|MM_{1}\| = \|M\|\|M_{1}\|$
3. $\|M^{-1}\| = \frac{1}{\|M\|}$
4. $\|I\| = 1$
5. $n \times n$ matrix에서 $\|\alpha M\| = \alpha^{n}\|M\|$
6. 두 행이나 열을 바꾸면 $\|M\|$의 부호가 바뀜
7. 한 행이나 열에 $\alpha$를 곱하면 determinant는 $\alpha\|M\|$
8. 두 행이나 열이 같으면 $\|M\| = 0$
9. Triangular matrix의 determinant는 사선의 항들을 곱한 결과와 같음

$$
\begin{vmatrix}
a_{1,1} & a_{1,2} & \dots  & a_{1,n} \\
0       & a_{2,2} & \dots  & a_{2,n} \\
\vdots  & \vdots  & \ddots & \vdots  \\
0       & 0       & \dots  & a_{n,n}
\end{vmatrix}
=
\begin{vmatrix}
a_{1,1} & 0       & \dots  & 0       \\
a_{2,1} & a_{2,2} & \dots  & 0       \\
\vdots  & \vdots  & \ddots & \vdots  \\
a_{n,1} & a_{n,2} & \dots  & a_{n,n}
\end{vmatrix}
=a_{1,1} a_{2,2} \dots a_{n,n}
$$



## Inverse

### Inverse의 특성


### Inverse가 존재하는 조건


### Singular Matrix


