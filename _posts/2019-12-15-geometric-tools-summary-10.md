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




## Frames


## Affine Transformations

### Types of Affine Maps

### Composition of Affine Maps


## Barycentric Coordinates and Simplexes

### Barycentric Coordinates and Subspaces

### Affine Independence

