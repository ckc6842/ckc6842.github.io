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
Point들의 집합 $\mathcal{P}$와 $n$차원의 vector space $\mathcal{V}$로 정의되는 affine space $\mathcal{A}$에 대해서,  
임의의 point $\mathcal{O} \in \mathcal{P}$와 basis $$\vec{v}_{1}, \vec{v}_{2}, \dots, \vec{v}_{n} \in \mathcal{V}$$ 를 선택했을 때,  
이는 $\mathcal{A}$에 대한 $frame^{2}$을 형성한다.  
Frame은 아래와 같이 표기한다.

$$
\mathcal{F} = (\vec{v}_{1}, \vec{v}_{2}, \dots, \vec{v}_{n}, \mathcal{O})^{T}
$$

Vector sapce $\mathcal{V}$에서는 해당 space에 포함되어 있는 어떤 vector $\vec{u}$ 도 basis vector들의 집합의 linear comination으로 나타낼 수 있다.

$$
\vec{u} = a_{1}\vec{v}_{1} + a_{2}\vec{v}_{2} + \cdots + a_{n}\vec{v}_{n}
$$

여기서 $a_{1}, a_{2}, \dots, a_{n}$은 $\vec{u}$의 *coordinates*이며 basis $\vec{v}_{1}, \vec{v}_{2}, \dots, \vec{v}_{n}$과 관계가 있다.

그렇다면 $\mathcal{P}$의 point들에 대해서는 어떨까?  
Point $\mathcal{P}$와 vector $\vec{u}$가 있을 때, $\mathcal{Q} = \mathcal{P} + \vec{u}$인 유일한 point가 존재한다.  
만약 $\mathcal{F}$에서 point $\mathcal{O}$를 $\mathcal{P}$로 고르면, point $\mathcal{Q} \in \mathcal{P}$는 특정 vector $\vec{u}$를 $\mathcal{O}$와 더한 것으로 정의할 수 있다.

$$
\begin{array}a
\mathcal{Q} & = & \vec{u} + \mathcal{O} \\
            & = & a_{1}\vec{v}_{1} + a_{2}\vec{v}_{2} + \cdots + a_{n}\vec{v}_{n} + \mathcal{O}
\end{array}
$$

마찬가지로 $\mathcal{Q}$의 coordinates들은 $a_{1}, a_{2}, \dots, a_{n}$이다.

## Affine Transformations

### Types of Affine Maps

### Composition of Affine Maps


## Barycentric Coordinates and Simplexes

### Barycentric Coordinates and Subspaces

### Affine Independence

