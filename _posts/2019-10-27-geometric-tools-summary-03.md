---
title: "Linear Space"
categories:
  - Computer Graphics
tags:
  - Linear Algebra
MathJax: true
---

## Fields
Field는 system 내에서 사칙연산을 수행할 수 있고, 결합법칙, 교환법칙, 분배법칙이 성립하는 대수적 요소들의 system을 말한다.  
일반적으로 field $F$는 set과 $+$, $*$ 두 가지의 연산으로 구성된다.

### Field $F$의 특성
1. $F$는 덧셈과 곱셈에 대해 닫혀있다: $\forall a,b \in F$, both $(a + b) \in F$ and $(a * b) \in F$
2. 덧셈과 곱셈에 대해 결합법칙이 성립한다: $\forall a,b,c \in F$, both $(a + b) + c = a + (b + c)$ and $(a * b) * c = a * (b * c)$
3. 덧셈과 곱셈에 대해 교환법칙이 성립한다: $\forall a,b \in F$, both $a + b = b + a$ and $a * b = b * a$
4. 덧셈에 대한 곱셈에 대해 분배법칙이 성립한다: $\forall a,b,c \in F$, both $a * (b + c) = (a * b) + (a * c)$ and $(b + c) * a = (b * a) + (c * a)$
5. 덧셈에 대한 항등원이 존재한다: $\exists 0 \in F$ such that $\forall a \in F, a + 0 = a$ and $0 + a = a$
6. 곱셈에 대한 항등원이 존재한다: $\exists 1 \in F$ such that $\forall a \in F, a * 1 = a$ and $1 * a = a$
7. 덧셈에 대한 역원이 존재한다: $\forall a \in F, \exists -a \in F$ such that $a + (-a) = 0$ and $(-a) + a = 0$
8. 곱셈에 대한 역원이 존재한다: $\forall a \neq 0 \in F, \exists a^{-1} \in F$ such that $a * a^{-1} = 1$ and $a^{-1} * a = 1$

## Linear Spaces
Linear space는 vector, scalar와 두 가지의 연산자로 구성된다.  

### Linear space의 특성
- Field $K$
- Vector 집합 $\mathcal{V}$
- $\vec{u},\vec{v} \in \mathcal{V}$에 대한 덧셈 연산자 $+$
- Scalar $k \in K$와 $\vec{v} \in \mathcal{V}$에 대한 곱셈 연산자 $*$  

에 대해 다음과 같은 특성을 가진다.

1. 곱셈에 대해 닫혀있다: $\forall k \in K$ and $\forall \vec{v} \in \mathcal{V}$, $k \vec{v} \in \mathcal{V}$
2. 덧셈에 대해 닫혀있다: $\forall \vec{u},\vec{v} \in \mathcal{V}$, $\vec{u} + \vec{v} \in \mathcal{V}$
3. 덧셈에 대한 결합법칙이 성립한다: $\forall \vec{u}, \vec{v}, \vec{w} \in \mathcal{V}$, $\vec{u} + (\vec{v} + \vec{w}) = (\vec{u} + \vec{v}) + \vec{w}$
4. 덧셈에 대한 항등원이 존재한다: $\forall \vec{v} \in \mathcal{V}$, $\exists \vec{0} \in \mathcal{V}$ (zero vector), such that $\vec{v} + \vec{0} = \vec{v}$
5. 덧셈에 대한 역원이 존재한다: $\forall \vec{v} \in \mathcal{V}$, $\exists -\vec{v}$, such that $\vec{v} + (-\vec{v}) = \vec{0}$
6. 덧셈에 대한 교환법칙이 성립한다: $\forall \vec{u},\vec{v} \in \mathcal{V}$, $\vec{u} + \vec{v} = \vec{v} + \vec{u}$
7. 덧셈에 대한 곱셈에 대해 분배법칙이 성립한다: $\forall k \in K$ and $\forall \vec{u},\vec{v} \in \mathcal{V}$, $k(\vec{u} + \vec{v}) = k\vec{u} + k\vec{v}$
8. 곱셈에 대한 덧셈에 대해 분배법칙이 성립한다: $\forall k_{1}, k_{2} \in K$ and $\forall \vec{v} \in \mathcal{V}$, $(k_{1} + k_{2})\vec{v} = k_{1}\vec{v} + k_{2}\vec{v}$
9. 곱셈에 대한 교환법칙이 성립한다: $\forall k_{1},k_{2} \in K$, and $\forall \vec{v} \in \mathcal{V}$, $(k_{1}k_{2})\vec{v} = k_{1}(k_{2}\vec{v})$
10. 곱셈에 대한 항등원이 존재한다: $\forall \vec{v} \in \mathcal{V}$, $1 * \vec{v} = \vec{v}$

## Linear Combinations and Span
*Linear combination*은 항들의 scalar 곱들의 합으로 이루어진 항들의 집합이다.  
$\mathbb{R}^{n}$에 속한 Vector 집합 $\mathcal{A}$: $\\{ \vec{a_{1}}, \vec{a_{2}},\dots, \vec{a_{n}} \\}$에서 vector $\vec{u} = k_{1}\vec{a_{1}} + k_{2}\vec{a_{2}} + \dots + k_{n}\vec{a_{n}}$와 같이 나타낼 수 있다.

Linear space $\mathcal{V}$에 정의된 vector 집합 $\\{ \vec{v_{1}}, \vec{v_{2}}, \dots, \vec{v_{n}} \\}$에 대해, vector들의 모든 linear combination 집합 $S$는 그 자체로 linear space이다.  
이 space는 $\\{ \vec{v_{1}}, \vec{v_{2}}, \dots, \vec{v_{n}} \\}$에 의해 *spanned* 되고, 이 집합을 $S$에 대한 *spanning set*이라 한다.  
여기서 중요한 아이디어는 $\vec{w} = k_{1}\vec{v_{1}} + k_{2}\vec{v_{2}} + \dots + k_{n}\vec{v_{n}}$에 대한 scalar $k_{1}, k_{2}, \dots, k_{n}$을 간단히 찾음으로써, vector $\vec(w) \in S$를  $\\{ \vec{v_{1}}, \vec{v_{2}}, \dots, \vec{v_{n}} \\}$의 관점에서 정리할 수 있다는 것이다.


## Linear Independence, Dimension, and Basis

### Linear Independence
- Vector space $\mathcal{V}$
- Vector 집합 $\\{ \vec{v_{1}}, \vec{v_{2}}, \dots, \vec{v_{n}} \\}$
- Constants $c_{1}, c_{2}, \dots, c_{n}$, not all 0

에 대해서

$$c_{1}\vec{v_{1}} + c_{2}\vec{v_{2}} + \dots + c_{n}\vec{v_{n}} = \vec{0}$$

이 모든 constants가 0일 때만 성립하면 vector 집합이 linearly independent하다고 한다.  
반면 0이 아닌 다른 constants들의 조합으로 위 식이 성립하면 linearly dependent하다고 한다.


### Basis and Dimension



