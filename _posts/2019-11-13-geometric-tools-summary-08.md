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

## Basis, Subspaces, Dimension

## Orientation

## Change of Basis

## Linear Transformations

