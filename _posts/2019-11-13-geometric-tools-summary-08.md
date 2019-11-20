---
title: "Vector Space"
categories:
  - Computer Graphics
tags:
  - Linear Algebra
MathJax: true
---

Vector는 다음과 같은 특성을 갖는다.
1. Vector 간의 덧셈(뺄셈)의 결과는 또 다른 vector이다.
2. 집합 $\mathcal{V}$는 linear combination에 대해 닫혀있다. $\vec{u}, \vec{v} \in \mathcal{V}$, $\alpha, \beta \in \mathbb{R}$일 때, $\alpha\vec{u} + \beta\vec{v} \in \mathcal{V}$가 성립한다.
3. Zero vector $\vec{0} \in \mathcal{V}$가 존재한다.
   1. $0 \in \mathbb{R}$일 때, $\forall\vec{v}, 0 \cdot \vec{v} = \vec{0}$
   2. $\forall\vec{v} \in \mathcal{V}, \vec{0} + \vec{v} = \vec{v}$

## Span
Vector 집합 $\\{ \vec{v_{1}}, \vec{v_{2}}, \cdots, \vec{v_{n}} \\} \in \mathcal{V}$에 대해, 이 vector들의 모든 linear combination의 집합 $S$는 다른 vector space로 구성된 vector들의 집합이다.  
이 space를 $\\{ \vec{v_{1}}, \vec{v_{2}}, \cdots, \vec{v_{n}} \\}$에 의해 *spanned* 되었다고 한다.  
즉, $\vec{w} \in S$인 모든 vector는 $\lambda_{i} \in \mathbb{R}$에 대해 $\vec{w} = \lambda_{1}\vec{v_{1}} + \lambda_{2}\vec{v_{2}} + \cdots + \lambda_{n}\vec{v_{n}}$와 같이 나타낼 수 있다.  
여기서 집합 $\\{ \vec{v_{1}}, \vec{v_{2}}, \cdots, \vec{v_{n}} \\}$는 $S$의 *spanning set*이라고 부른다.

## Linear Independence
앞선 linear space에서 살펴본 것과 같이 vector space에서의 linear independence도 유사하게 정의한다.  
집합 $\\{ \vec{v_{1}}, \vec{v_{2}}, \cdots, \vec{v_{n}} \\} \in \mathcal{V}$는 

$$
\lambda_{1}\vec{v_{1}} + \lambda_{2}\vec{v_{2}} + \cdots + \lambda_{n}\vec{v_{n}} = \vec{0}
$$

가 $\lambda_{1} = 0, \lambda_{2} = 0, \cdots, \lambda_{n} = 0$ 인 경우에만 성립하면 *linearly independent*하다.  
다시 말하자면, $\vec{v_{i}}$가 집합 내의 다른 vector들의 linear combination이 아닌 경우에 linearly independent하다고 할 수 있다.

## Basis, Subspaces, Dimension
Vector space S에 대해 집합 $\\{ \vec{v_{1}}, \vec{v_{2}}, \cdots, \vec{v_{n}} \\}$이
1. $\\{ \vec{v_{1}}, \vec{v_{2}}, \cdots, \vec{v_{n}} \\}$는 linearly independent
2. $\\{ \vec{v_{1}}, \vec{v_{2}}, \cdots, \vec{v_{n}} \\}$는 S의 spanning set
이면 S의 *basis*이다.

Vector space $\mathcal{V}$, basis vector 집합 $V = \\{ \vec{v_{1}}, \vec{v_{2}}, \cdots, \vec{v_{n}} \\} \in \mathcal{V}$에 대해 $V$에 의해 spanned 된 space $S$는 $\mathcal{V}$의 *subspace*라고 한다.  
그리고 $S$ 내의 linearly independent한 vector의 최대 개수를 $S$의 *dimension n*이라고 한다.

Linearly independent한 vector 집합 $V = \\{ \vec{v_{1}}, \vec{v_{2}}, \cdots, \vec{v_{n}} \\} \in \mathcal{V}$을 가정해보자.  
$V$에 의해 spanned 되는 space 내의 vector $\vec{w}$는 $V$의 linear combination으로 나타낼 수 있다.

$$
\vec{w} = x_{1}\vec{v_{1}} + x_{2}\vec{v_{2}} + \cdots + x_{n}\vec{v_{n}}, x_{i} \in \mathbb{R}
$$

Linearly independent 하기 위해서는 주어진 $\vec{w}$에 대해 $x_{i}$는 고유해야 한다.  
<!-- $V = \\{ \vec{v_{1}}, \vec{v_{2}}, \cdots, \vec{v_{n}} \\} \in \mathcal{V}$ -->
여기서 $x_{i}\vec{v_{i}}$를 $\vec{w}$의 *components*라고 부르고, 계수 $x_{i}$를 $\vec{w}$의 *coordinates*라고 부른다.

$\vec{u}, \vec{v}$가 span하는 Space $\mathcal{V}$ 상에 있는 vector $\vec{w}$는 
basis vector들의 고유한 linear combination으로 나타낼 수 있다(예: $\vec{w} = 3\vec{u} + 2\vec{v}$).

## Orientation
Linearly independent한 두 3차원 vector $\vec{u}, \vec{v}$는 앞서 살펴본 것과 같이 2차원 space 내에 존재한다.  
이 때 두 vector는 $\theta_{\vec{u}\vec{v}}$의 각을 이룬다.  
일반적으로 두 vector의 각도는 vector가 쓰여진 순서로 다루고, 2차원 공간 상에서 반시계 방향으로 양의 크기를 가진다.  
하지만 3차원으로 놓고 보면 이 2차원 공간은 바라보는 시점에 따라 방향이 반대가 될 수 있다.

이제 3차원 공간 상에 존재하는 세 개의 3차원 vector가 이루는 각도를 생각해보자.  
Linealy independent한 $\vec{u}, \vec{v}, \vec{w}$가 있을 때 basis에 대한 각도 *sign*은 다음과 같이 정의할 수 있다.

$$
sgn(\vec{u}, \vec{v}, \vec{w}) = sgn(\theta_{\vec{u}\vec{v}})
$$

일반적으로 3차원 공간에서 각도의 방향을 따질 때는 "오른 손의 법칙"을 따른다.  
엄지가 가리키는 방향에 따라 나머지 네 손가락이 가리키는 방향이 각도의 양의 크기를 갖게 된다.


## Change of Basis
앞서 살펴본 바와 같이 특정 space 내의 모든 vector들은 basis vector들의 집합으로 이루어진 고유한 linear combination를 갖는다.  
하지만 이는 모든 vector가 고유한 linear combination을 갖는다는 뜻은 아니다.  
$n$차원 vector sapce $\mathcal{V}$에 대해, $\mathcal{V}$에 linearly independent한 $n$-ary 부분 집합의 수는 무한히 많다.  
즉, $\vec{w} \in \mathcal{V}$는 임의로 고른 basis bector 집합의 linear combination으로 표현할 수 있다는 뜻이다.  

$\mathcal{V}$에 대한 basis vector 집합 $\vec{a_{1}}, \vec{a_{2}}, \dots, \vec{a_{n}}$와 $\vec{b_{1}}, \vec{b_{2}}, \dots, \vec{b_{n}}$을 가정해보자.  
$\mathcal{V}$내의 어느 vector든 basis vector 들로 표현할 수 있고, 또한 이 vector는 basis vector들의 또 다른 집합을 만든다.  
즉, $\vec{a}$의 각각은 $\vec{b}$로 구성된 basis로 표현할 수 있다.

$$
\vec{a_{k}} = c_{1,k}\vec{b_{1}} + c_{2,k}\vec{b_{2}} + \cdots + c_{n,k}\vec{b_{n}}
$$

여기서 $\vec{w} \in \mathcal{V}$는 $\vec{a_{1}}, \vec{a_{2}}, \dots, \vec{a_{n}}$의 linear combination에 $\vec{a_{k}}$로 구성된 상기 식을 대입한 형태로 나타낼 수 있다.

$$
\begin{aligned}
& \vec{w} & = & d_{1}\vec{a_{1}} + d_{2}\vec{a_{2}} + \cdots + d_{n}\vec{a_{n}} \\
&         & = & d_{1}(c_{1,1}\vec{b_{1}} + c_{2,1}\vec{b_{2}} + \cdots + c_{n,1}\vec{b_{n}}) \\
&         &   & + d_{2}(c_{1,2}\vec{b_{1}} + c_{2,2}\vec{b_{2}} + \cdots + c_{n,2}\vec{b_{n}}) \\
&         &   & + \cdots + d_{n}(c_{1,n}\vec{b_{1}} + c_{2,n}\vec{b_{2}} + \cdots + c_{n,n}\vec{b_{n}}) \\
&         & = & (d_{1}c_{1,1} + d_{2}c_{1,2} + \cdots + d_{n}c_{1,n})\vec{b_{1}} \\
&         &   & + (d_{1}c_{2,1} + d_{2}c_{2,2} + \cdots + d_{n}c_{2,n})\vec{b_{2}} \\
&         &   & + \cdots + (d_{1}c_{n,1} + d_{2}c_{n,2} + \cdots + d_{n}c_{n,n})\vec{b_{n}} \\
\end{aligned}
$$

## Linear Transformations
Vector space에서의 linear transformation은 한 vecotr space를 다른 vector space로 mapping 하는 것을 의미한다.  
공식적으로, 두 vector space $\mathcal{U}, \mathcal{V}$ 간의 linear transformation은 아래와 같은 조건을 만족하는 map $\mathcal{T}: \mathcal{U} \rightarrow \mathcal{V}$이다.
1. 모든 vector $\vec{u}, \vec{v} \in \mathcal{V}$에 대해, $T(\vec{u} + \vec{v}) = T(\vec{u}) + T(\vec{v})$
2. 모든 $\alpha \in \mathbb{R}$와 $\vec{u} \in \mathcal{V}$에 대해, $T(\alpha\vec{u} = \alpha T(\vec{u})$

Linear transformation은 *preserve linear combination*이라고 부르기도 한다.  
