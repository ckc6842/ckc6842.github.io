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

### 데카르트 좌표계의 Frames

모든 vector $\vec{v}$는 *unit vector* $\hat{v}$ 와 관계가 있다.  
Unit vector는 $\vec{v}$와 방향은 같지만, 길이가 1인 vector이다.  
즉, unit vector는 $\vec{v}$를 그 길이로 나누면 구할 수 있다.

$$
\hat{v} = \frac{\vec{v}}{||\vec{v}||}
$$

이를 통해 basis vector들이 

## Affine Transformations
*Affine transformation*은 어떤 affine space에 있는 point들과 vector들을 다른 affine space로 mapping 하는 것을 말한다.
일반적으로, $T: \mathcal{A}^{n} \mapsto \mathcal{B}^{m}$가 affine transformation이려면, affine combination을 유지하고, $P_{i} \in \mathcal{A}$와 $\sum_{i=1}^{n}a_{1} = 1$을 만족해야 한다.

$$
T(a_{1}P_{1} + a_{2}P_{2} + \cdots + a_{n}P_{n}) = a_{1}T(P_{1}) + a_{2}T(P_{2}) + \cdots + a_{n}T(P_{n})
$$

주의해야 할 점은 차원 n과 m은 꼭 같을 필요는 없지만, $m \leq n$이 성립해야 한다.  
그 이유는 affine transformation이 geometric object들을 대응되는 object들에 mapping하기 때문이다.

앞서 affine combination에 대한 내용에서 point $R$을 같은 line 상에 있는 point $P$와 $Q$의 affine combination으로 나타내는 것을 보았다.

$$
R = (1 - \alpha)P + \alpha Q
$$

여기에 affine tranformation을 적용하면 다음과 같다.

$$
\begin{array}a
T(R) & = & T((1 - \alpha)P + \alpha Q)\\
     & = & (1 - \alpha)T(P) + \alpha T(Q)
\end{array}
$$

이는 아래와 같이 line의 equation을 parametric equation으로 작성한 것과 매우 유사하다.

$$
R(t) = (1 - t)P + tQ
$$

상기 수식에 T를 적용하면 다음과 같다.

$$
\begin{array}a
T(R(t)) & = & T((1 - t)P + tQ)
        & = & (1 - t)T(P) + tT(Q)
\end{array}
$$

즉, line의 parametric equation은 $P$와 $Q$에 의해 정의된다.  
위 과정에서 상수들이 transformation T의 영향을 받지 않은 점이 중요한 점이다.


### Types of Affine Maps

### Composition of Affine Maps


## Barycentric Coordinates and Simplexes

### Barycentric Coordinates and Subspaces

### Affine Independence

