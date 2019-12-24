---
title: "Affine Space 2"
categories:
  - Computer Graphics
tags:
  - Linear Algebra
MathJax: true
---


## Volume, The Determinant, and The Scalar Triple Product
Linearly independent한 세 vector $\vec{u}, \vec{v}, \vec{w}$가 만드는 평행 육면체의 부피는 다음과 같이 나타낸다.

$$
Vol(\vec{u}, \vec{v}, \vec{w})
$$

이 때, vector 간의 순서가 바뀌어도 같은 평행 육면체를 만드므로, 순서는 중요하지 않다.

$Vol(\vec{u}, \vec{v}, \vec{w})$의 정의는 다음과 같다.

$$
\begin{array}a
Vol(\vec{u}, \vec{v}, \vec{w}) & = & base * height \\
& = & ||\vec{u}||||\vec{v}||sin\psi * ||\vec{w}|||cos\theta| \\
& = & ||\vec{u}||||\vec{v}||sin\psi * ||\vec{w}_{\||}|| \\
& = & ||\vec{u} \times \vec{v}|| * ||\vec{w}_{\||}|| \\
& = & ||\vec{u} \times \vec{v} \cdot \vec{w}_{\||}|| \\
& = & ||\vec{u} \times \vec{v} \cdot \vec{w}_{\||}|| \\
& = & ||\vec{u} \times \vec{v} \cdot \vec{w}||
\end{array}
$$

위 수식은 방향에 따라 두 가지 경우로 나뉜다.

$$
Vol(\vec{u}, \vec{v}, \vec{w})=
\begin{cases}
  1 & \Longleftrightarrow 0 \\
  1 & \Longleftrightarrow 0 \\
\end{cases}
$$

오른손 법칙에 따라서

$$
sgn(\vec{u}, \vec{v}, \vec{w}) = sgn(\vec{u}, \vec{v}, \vec{w}_{||})= 
\begin{cases}
  +1 & \Longleftrightarrow \vec{w}_{||} || \vec{u}\times\vec{v} \\
  -1 & \Longleftrightarrow \vec{w}_{||} || -\vec{u}\times\vec{v} \\
\end{cases}
$$

이므로 수식은 다음과 같이 정리할 수 있다.

$$
Vol(\vec{u}, \vec{v}, \vec{w}) = sgn(\vec{u}, \vec{v}, \vec{w})((\vec{u}\times\vec{v})\cdot\vec{w})
$$

여기서 $(\vec{u}\times\vec{v})\cdot\vec{w}$는 보통 *scalar triple product*라고 부르고, 이는 $\vec{u}, \vec{v}, \vec{w}$가 순서대로 행/열로 나열된 matrix의 determinant이다.

$$
det(\vec{u}, \vec{v}, \vec{w})
$$

즉, 정리된 수식에 대입하면 부피는 *signed* determinant라고 할 수 있다.

$$
Vol(\vec{u}, \vec{v}, \vec{w}) = |det(\vec{u}, \vec{v}, \vec{w})| = sgn(\vec{u}, \vec{v}, \vec{w})det(\vec{u}, \vec{v}, \vec{w})
$$

Determinent, scalar triple product, 부피와 관련된 또다른 속성들은 다음과 같다.
1. Determinant $det(\vec{u}, \vec{v}, \vec{w})$는 집합 $\{\vec{u}, \vec{v}, \vec{w}\}$이 basis를 이룰때만 0이 아니다.
   예를 들어 3차원 공간에서 세 vector가 basis를 이루지 않으면, 세 vector는 부피가 없는 면이나 선을 span한다.
2. Determinant $det(\vec{u}, \vec{v}, \vec{w})$는 $(\vec{u}, \vec{v}, \vec{w})$의 sign이 0보다 클 때만 양수이다.
3. Vector 간의 순환하는 순서 변경은 determinant 값에 영향이 없다.
   $det(\vec{u}, \vec{v}, \vec{w}) = det(\vec{w}, \vec{u}, \vec{v}) = det(\vec{v}, \vec{w}, \vec{u})$
4. Vector 간의 순서가 뒤집어지면 determinant의 부호가 바뀌지만 크기는 변함이 없다.
   $det(\vec{u}, \vec{v}, \vec{w}) = -det(\vec{w}, \vec{v}, \vec{u}) = -det(\vec{v}, \vec{u}, \vec{w}) = -det(\vec{u}, \vec{w}, \vec{v})$
5. 한 vector의 부호가 뒤집어지면 determinant의 부호가 바뀐다.
   $det(\vec{u}, \vec{v}, \vec{w}) = -det(-\vec{u}, \vec{v}, \vec{w}) = -det(\vec{u}, -\vec{v}, \vec{w}) = -det(\vec{u}, \vec{v}, -\vec{w})$
6. 한 vector에 scalar 곱을 하면 determinant도 그만큼 커진다.
   $det(c\vec{u}, \vec{v}, \vec{w}) = det(\vec{u}, c\vec{v}, \vec{w}) = det(\vec{u}, \vec{v}, c\vec{w}) = c det(\vec{u}, \vec{v}, \vec{w})$
7. 오른손 basis vector들의 orthonormal space는 unit determinant를 갖는다.



## Frames


## Affine Transformations

### Types of Affine Maps

### Composition of Affine Maps


## Barycentric Coordinates and Simplexes

### Barycentric Coordinates and Subspaces

### Affine Independence

