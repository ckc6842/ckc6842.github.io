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
Scalar product는 일반적으로 *dot product*로 많이 알려져 있는 *inner product*의 일종이다.  
이 챕터에서 알아야 할 주요 기호들은 다음과 같다.

* $\vec{u}$의 길이: $\|\|n\|\|$
* $\vec{u}$의 방향: dir$(\vec{u})$
* Scalar의 부호: sgn$(\alpha)$
* $\vec{u}$와 $\vec{v}$가 수직: $\vec{u}\perp\vec{v}$
* $\vec{u}$와 $\vec{v}$가 평행: $\vec{u} \|\| \vec{v}$

Scalar product 전에 vector 간의 *projection*에 대해 먼저 알아보자.  

두 vector $\vec{u}, \vec{v}$가 있을 때 두 vector 사이의 거리를 $\theta$라 하자.  
Vector $\vec{v}$는 $\vec{u}$와 관련된 두 요소로 나타낼 수 있다.

* $\vec{u}$로의 수직 vector $\vec{v}_{\perp}$: *normal component*
* $\vec{u}$로의 수평 vector $\vec{v}_{\|\|}$: *orthogonal projection*

여기서 $$\vec{v}_{\perp} + \vec{v}_{\|} = \vec{v}$$ 이다.  

먼저 $\vec{v}_{\perp}$와 $$\vec{v}_{\|}$$의 길이를 살펴보자

$$
\|\vec{v}_{\perp}\| = \|\vec{v}\| |sin\theta| \\
\|\vec{v}_{\|}\| = \|\vec{v}\| |cos\theta|
$$

$\hat{u} = \frac{\vec{u}}{\|\|\vec{u}\|\|}$가 unit vector이고 $\vec{u}$와 같은 방향일 때,

$$
\vec{v}_{\|} = \|\vec{v}\|cos\theta\hat{u}
$$

가 성립한다.  

Dot product는 다음과 같은 중요한 특성들을 가지고 있다.

1. 정의: $\vec{u}\cdot\vec{v} = \|\|\vec{u}\|\|\|\|\vec{v}\|\|cos\theta$
2. 쌍선형: $\forall\alpha\beta \in \mathbb{R}$, $\forall\vec{u},\vec{v},\vec{w} \in \mathcal{A}.\mathcal{V}$,
   1. $(\alpha\vec{u} + \beta\vec{v})\cdot\vec{w} = \alpha(\vec{u}\cdot\vec{w}) + \beta(\vec{v}\cdot\vec{w})$
   2. $\vec{u}\cdot(\alpha\vec{v} + \beta\vec{w}) = \alpha(\vec{u}\cdot\vec{v}) + \beta(\vec{u}\cdot\vec{w})$
3. Positive definiteness
   1. $\forall\vec{u} \in \mathcal{A.V}, \vec{u} \neq \vec{0}, \vec{u}\cdot\vec{u} \gt 0$
   2. $\vec{0}\cdot\vec{0} = 0$
4. 교환법칙: $\vec{u}\cdot\vec{v} = \vec{v}\cdot\vec{u}$
5. vector 덧셈에 대한 dot product의 분배법칙: $\vec{u}\cdot(\vec{v} + \vec{w}) = (\vec{u}\cdot\vec{v}) + (\vec{u}\cdot\vec{w})$
6. dot product에 대한 vector 덧셈의 분배법칙: $(\vec{u} + \vec{v})\cdot\vec{w} = \vec{u}\cdot\vec{w} + \vec{v}\cdot\vec{w}$

따라서 위 내용을 정리하면 다음과 같다
1. 제곱 길이: $\vec{u}\cdot\vec{u} = \|\|\vec{u}\|\|^{2}$
2. 각도: $\theta = cos^{-1}\frac{\vec{u}\cdot\vec{v}}{\|\|\vec{u}\|\|\|\|\vec{v}\|\|}$
3. projection: $\vec{v}_{\|\|} = \frac{(\vec{u}\cdot\vec{v})\vec{u}}{\vec{u}\cdot\vec{u}}$
4. normal: $\vec{v}_\perp = \vec{v} - \frac{(\vec{u}\cdot\vec{v})\vec{u}}{\vec{u}\cdot\vec{u}}$
5. 수직: $\vec{u}\cdot\vec{v} = 0 \Longleftrightarrow \vec{u} \perp \vec{v}$

### Vector Product
Vector pruduct는 *cross product*라고도 부른다.  
Dot product와 마찬가지로 cross product도 두 vector 간의 각도와 관련이 있지만, 두 시작점이 맞닿아있는 vector가 만드는 평행사변형의 넓이를 정의하기도 한다.  

평행하지 않은 두 vector $\vec{u}, \vec{v}$가 있을 때 이를 2차원 평면으로 정의할 수 있다.  
만약 이 평면이 종이 위에 놓인 것이 아니라 공간 위에 떠있다고 생각해보면, dot product는 두 vector간의 각도는 구할 수 있지만 공간 상에 평면의 방향은 결정할 수 없다.  

두 vector $\vec{u}, \vec{v}$의 cross product는 또 다른 vector $\vec{w}$로 정의할 수 있다.  
$\vec{w}$는 $\vec{u}, \vec{v}$를 포함하는 평면에 수직이고, 길이는 두 vector 사이의 각도와 관련이 있다.  
Cross product는 $\times$로 나타낸다.  
정의와 관련된 특성들은 다음과 같다.  
1. 두 vector의 cross product $\vec{w} = \vec{u}\times\vec{v}는 vector이다.$
2. 두 vector의 cross product는 두 vector에 수직이다: dir$(\vec{u}\times\vec{v})\perp\vec{u},\vec{v}$
3. 두 vector의 cross pruduct의 길이는 $\vec{u}, \vec{v}$로 이루어진 평행사변형의 넓이와 같다: $\|\|\vec{u}\times\vec{v}\|\| = Area(\vec{u}, \vec{v}) = \|\|\vec{u}\|\| \|\|\vec{v}\|\|sin\theta$
   1. 만약 $\theta > 0$이면 넓이는 양수이고, $\theta < 0$이면 넓이는 음수이다. 따라서 만약 부호가 없는 넓이가 필요하다면 $sin\theta$의 절대 값을 사용해야 한다.

$\vec{u}, \vec{v}$로 이루어진 평면에 수직인 vector는 윗 방향과 아랫 방향이 있다.  
오른손 법칙에 따라 $\vec{u}, \vec{v}$ 사이의 각도 $\theta > 0$이면, cross product vector는 페이지 바깥쪽을 가리기고, $\theta < 0$이면 안쪽을 가리킬 것이다.

Vector product의 또 다른 특성들은 다음과 같다.
1. 교환법칙이 성립하지 않는다: $\vec{u}\times\vec{v} \neq \vec{v}\times\vec{u}$
2. 분배 법칙이 성립한다.
   1. $\vec{u}\times(\vec{v} + \vec{w}) = (\vec{u}\times\vec{v}) + (\vec{u}\times\vec{v})$
   2. $(\alpha\vec{u})\times\vec{v} = \vec{u}\times(\alpha\vec{v}) = \alpha(\vec{u}\times\vec{v})$
3. 평행성: $\vec{u}\|\|\vec{v} = \Longleftrightarrow \vec{u}\times\vec{v} = \vec{0}$


## Volume, The Determinant, and The Scalar Triple Product


## Frames


## Affine Transformations

### Types of Affine Maps

### Composition of Affine Maps


## Barycentric Coordinates and Simplexes

### Barycentric Coordinates and Subspaces

### Affine Independence

