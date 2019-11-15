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
여기서 $x_{i}\vec{v_{i}}$를 $\vec{w}$의 *components*라고 부르고, 계수 $x_{i}$를 $vec{w}$의 *coordinates*라고 부른다.

## Orientation

## Change of Basis

## Linear Transformations

