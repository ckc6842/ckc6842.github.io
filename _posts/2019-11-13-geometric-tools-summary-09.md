---
title: "Affine Space"
categories:
  - Computer Graphics
tags:
  - Linear Algebra
MathJax: true
---

Point와 vector의차이
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

### Affine Combinations


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

