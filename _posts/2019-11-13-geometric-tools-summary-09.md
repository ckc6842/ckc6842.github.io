---
title: "Affine Space"
categories:
  - Computer Graphics
tags:
  - Linear Algebra
MathJax: true
---

Vector는 일반적으로 $(\vec{u}, \vec{v})$ 혹은, vector의 unit length를 나타내는 hat $(\hat{u}, \hat{v})$와 같이 표현한다.  
반면 point는 $(P, Q)$와 같이 대문자로 나타낸다.  
또한 vector는 두 point $P$로부터 $Q$로의 $\vec{pq}$와 같이 나타낼 수 있다.

공식적으로 *affine space* $\mathcal{A}$는 point들의 집합 $\mathcal{P}$와 vector들의 집합 $\mathcal{V}$로 구성되며, $\mathcal{A}$는 $\mathcal{V}$의 basis들, 혹은 일부 basis로 span 된 vector space이다.  
$\mathcal{A}$의 차원 $n$은 $\mathcal{V}$의 차원이다.  
앞으로 $\mathcal{A}$의 point들은 $\mathcal{A.P}$, vector들은 $\mathcal{A.V}$라고 부를 것이다.  
Affine space의 point space와 *underlying* vector space 간의 관계는 *Head-to-Tail Axiom*이라고 부르는 point들의 짝들의 뺄셈으로 정의되는 공리로 정의된다.  
1. $\forall P, Q \in A.P, \exists$ a unique vector $\vec{v} \in \mathcal{A}$. $\vec{V}$ such that $\vec{v} = P - Q$
2. $\forall Q \in A.P, \forall\vec{v} \in A.V, \exists$ a unique point $P$ such that $P - Q = \vec{v}$
3. $\forall P, Q, R \in \mathcal{A.P}, (P - Q) + (Q - R) = P - R$

1.은 $P = Q + \vec{v}$와 같이 표현할 수 있고, 또한 $P = P + \vec{0}$임을 내포하고 있다.

점들 간의 두 가지 중요한 곱셈 연산을 정의하는, *Coordinate Axiom*이라는 또 다른 공리가 있따.

$\forall P \in \mathcal{A}.\mathcal{P}, 1 \cdot P = P$ and $0 \cdot P = \vec{0}$

즉, point에 1을 곱하면 point가 되고, 0을 곱하면 zero vector가 된다는 것이다.

또한 몇 가지 중요한 등식들이 있다.
1. $Q - Q = \vec{0}$
2. $R - Q = -(Q - R)$
3. $\vec{v} + (Q - R) = (Q + \vec{v}) - R$
4. $Q - (R + \vec{v}) = (Q - R) - \vec{v}$
5. $P = Q + (P - Q)$
6. $(Q + \vec{v}) - (R + \vec{w}) = (Q - R) + (\vec{v} - \vec{w})$

### Affine Combinations
앞서 살펴본 연산들을 정리하면 다음과 같다.
* 두 vector를 더하면 또 다른 vector가 나온다.
* vector를 scalar로 곱하면 vector가 된다.
* point에 vector를 더하면 또다른 point가 나온다.
* 두 point를 빼면 vector가 된다.

한편 다음과 같은 연산은 아직 확인하지 않았다.
* point를 scalar로 곱하기
* 두 point를 더하기

첫 번째 연산은 location을 *scale* 하는 것이 어떠한 의미를 갖는가?  
두 번째 연산 역시 의미있는 해석을 할 수 없다.

하지만, *affine combination*에서는 두 point를 더하는 것과 같은 연산이 존재한다.  
두 point $P, Q$와 그 사이에 존재하는 임의의 점 $R$을 가정해보자.  
$R$은 $P, Q$를 잇는 vector를 특정 비율 $\alpha: 1 - \alpha$로 나눈다고 하자.  

$$
R = P + \alpha(Q - P)
$$

위 식을 정리하면 

$$
R = (1 - \alpha)P + \alpha Q
$$

로 나타낼 수 있고 $\alpha_{1} + \alpha_{2} = 1$로 치환하면,

$$
R = \alpha_{1}P + \alpha_{2}Q
$$

로 정리할 수 있다.  
위 식을 보면 존재 할 수 없는 point의 scalar 곱셈과 point 간의 덧셈을 볼 수 있다.  
하지만 이 식은 최초의 affine combination을 정리한 것이므로 기술적으로는 문제되지 않는다.  

$\alpha$를 0과 1사이로 설정했다면, point $R$은 $P, Q$ 사이에 위치할 것이 분명하다.  
이러한 경우를 *convex combination*이라 한다.  

위에서 본 것을 두 point 이상의 affine combination으로 확장할 수 있다.
주어진 n개의 point $P_{1}, P_{2}, \cdots, P_{n}$과, 총 합이 1인 $n$개의 실수 $\alpha_{1}, \alpha_{2}, \cdots, \alpha_{n}$에 대해 affine combination을 다음과 같이 정의할 수 있다.  

$$
P_{1} + \alpha_{2}(P_{2} - P_{1}) + \alpha_{3}(P_{3} - P_{1}) + \cdots + \alpha_{n}(P_{n} - P_{1})
$$

이를 다시 정리하면 다음과 같다.

$$
\alpha_{1}P_{1} + \alpha_{2}P_{2} + \cdots + \alpha_{n}P_{n}
$$

## Euclidian Geometry

### Scalar Product

### Vector Product


## Volume, The Determinant, and The Scalar Triple Product


## Frames


## Affine Transformations

### Types of Affine Maps

### Composition of Affine Maps


## Barycentric Coordinates and Simplexes

### Barycentric Coordinates and Subspaces

### Affine Independence

