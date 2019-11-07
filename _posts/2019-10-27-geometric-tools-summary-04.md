---
title: "Linear Mapping"
categories:
  - Computer Graphics
tags:
  - Linear Algebra
MathJax: true
---

## 일반적인 Mapping
원소들의 짝들을 나타내는 용어인 *mapping*, *function*, *transformation*은 동의어이다.

### 정의
$\mathcal{A} = \\{ a_{1}, a_{2}, \dots, a_{m} \\}$, $\mathcal{B} = \\{ b_{1}, b_{2}, \dots, b_{m} \\}$ 일 때,  
$\mathcal{A}$부터 $\mathcal{B}로의$ *function* $T$는 $a \in \mathcal{A}, b \in \mathcal{B}$인 $(a, b)$ 쌍들의 집합이고, 다음과 같이 표현한다.  

$$T: \mathcal{A} \rightarrow \mathcal{B}$$

각각의 쌍들은 고유하고, $a \in \mathcal{A}$ 원소들은 오직 한 쌍만 갖는다.  
여기서 $\mathcal{A}$는 *domain*, $\mathcal{B}$는 *range* 혹은 *co-domain*이라 부른다.

$a \in \mathcal{A}$ 원소에 대해 $a$와 짝을 이루는 $\mathcal{B}$의 값은 $T(a)$ 혹은 $aT$로 표현하고, $a$의 *image*라 부른다.  
$b \in \mathcal{B}$ 원소가 $a \in \mathcal{A}$ 의 image일 때, $a$는 $b$의 *preimage*라 부른다.  
$a \in \mathcal{A}$인 모든 원소는 쌍으로 나타나야 하지만, $b \in \mathcal{B}$는 그렇지 않다.

### Composition of Mappings
Function $T: \mathcal{A} \rightarrow \mathcal{B}$ 에서 모든 $a \in \mathcal{A}$에 대해 $T(a) = b$인 $b \in \mathcal{B}$가 존재한다.  
마찬가지로, function $U: \mathcal{B} \rightarrow \mathcal{C}$는 원소 $b$($a$의 image)를 $c \in \mathcal{C}$인 원소에 대응시킨다.   
두 function $T, U$를 $a$에 적용하는 것을 $T$와 $U$의 *composition*이라 부르고, 아래와 같이 표현한다.

$$(U \circ T)(a) = U(T(a))$$

그리고 원소의 mapping은 $a \mapsto U(T(a))$ 와 같이 표현한다.

Mappings의 composition은 결합법칙이 성립한다. 따라서  
- Function $T: \mathcal{A} \rightarrow \mathcal{B}$
- Function $U: \mathcal{B} \rightarrow \mathcal{C}$
- Function $V: \mathcal{C} \rightarrow \mathcal{D}$

가 있을 때, $(V \circ U) \circ T = V \circ (U \circ T)$가 성립한다.

### Mapping의 특별한 종류
Mapping에는 세 가지 중요한 종류인 *one-to-one*, *onto*, *isomorphic*이 있다.  
- One-to-one mapping $T: \mathcal{A} \rightarrow \mathcal{B}$ $\Rightarrow$ 모든 $a \in \mathcal{A}$가 고유한 $b \in \mathcal{B}$와 대응 될 때
- Onto mapping $T: \mathcal{A} \rightarrow \mathcal{B}$ $\Rightarrow$ 모든 $b \in \mathcal{B}$가 $a \in \mathcal{A}$의 image 일 때(여러 a의 image일 수도 있음)
- Isomorphic mapping $T: \mathcal{A} \rightarrow \mathcal{B}$ $\Rightarrow$ one-to-one이면서 onto인 mapping

### Inverse Mappings
Mapping $T: \mathcal{A} \rightarrow \mathcal{B}$ 에 대해 $TT^{-1} = I$ ($I$는 identity mapping)인 $T^{-1}: \mathcal{B} \rightarrow \mathcal{A}$가 존재하면 $T^{-1}$을 $T$의 *inverse mapping*이라 한다.  
$T^{-1}$에서는 $\mathcal{B}$가 domain이 되고, 모든 원소 $a \in \mathcal{A}$가 반드시 $T^{-1}$의 range여야 한다.  
즉, mapping $T$가 one-to-one이면서 onto여야 invertible하다.


## Linear Mappings
Linear space $\mathcal{A}, \mathcal{B}$에 대해, linear mapping $T: \mathcal{A} \rightarrow \mathcal{B}$은 vector 합과 scalar 곱셈을 유지하는 function이다.

1. $\forall \vec{u}, \vec{v} \in \mathcal{A}, T(\vec{u} + \vec{v}) = T(\vec{u}) + T(\vec{v})$
2. $\forall \alpha \in \mathbb{R}$ and $\forall \vec{v} \in \mathcal{A}, T(\alpha \vec{v}) = \alpha T(\vec{v})$

주목해야 하는 점은 linear mapping이 linear combination을 유지한다는 것이다.  
즉 $T(\alpha \vec{u} + \beta \vec{v}) = \alpha T(\vec{u}) + \beta T(\vec{v})$가 성립한다.  
One-to-one이면서 onto인 linear function $T: \mathcal{A} \rightarrow \mathcal{B}$를 *isomorphism*이라 한다.


## Linear Mappings의 Matrix 표현
$\mathbb{R}^{m}$에서 $\mathbb{R}^{n}$으로의 linear mapping은 matrix로 표현할 수 있다.  
즉, $\mathcal{A}$에 속한 vector가 $\mathcal{B}$에 속하는 vector에 어떻게 대응되는지 matrix를 통해 나타낼 수 있다.

Basis vectors $\vec{u_{1}}, \vec{u_{2}}, \dots, \vec{u_{m}}$을 가진 linear space $\mathcal{A}$와, $\vec{v_{1}}, \vec{v_{2}}, \dots, \vec{v_{m}}$를 가진 $\mathcal{B}$에 대해 linear mapping $T: \mathcal{A} \rightarrow \mathcal{B}$를 가정해보자.  
Map 된 base vectors $T(\vec{u_{1}}), T(\vec{u_{2}}), \dots, T(\vec{u_{m}})$는 $\mathcal{B}$의 원소이다.  
따라서 이는 $\mathcal{B}$의 basis vectors $\vec{v_{1}}, \vec{v_{2}}, \dots, \vec{v_{m}}$의 linear combination으로 표현할 수 있다.

$$
T(\vec{u_{1}}) = a_{1,1}\vec{v_{1}} + a_{1,2}\vec{v_{2}} + \dots + a_{1,n}\vec{v_{n}} \\
T(\vec{u_{2}}) = a_{2,1}\vec{v_{1}} + a_{2,2}\vec{v_{2}} + \dots + a_{2,n}\vec{v_{n}} \\
\vdots \\
T(\vec{u_{m}}) = a_{m,1}\vec{v_{1}} + a_{m,2}\vec{v_{2}} + \dots + a_{m,n}\vec{v_{n}} \\
$$

위 linear combination의 coefficient들을 이용해 $T$를 matrix로 표현할 수 있다.

$$
T = 
\begin{bmatrix}
a_{1,1} & a_{1,2} & \dots  & a_{1,n} \\
a_{2,1} & a_{2,2} & \dots  & a_{2,n} \\
\vdots  & \vdots  & \ddots & \vdots  \\
a_{m,1} & a_{m,2} & \dots  & a_{m,n}
\end{bmatrix}
$$

위 결과에서 두 가지 중요한 점을 확인할 수 있다.

1. $\mathcal{A}$에 속한 vector의 matrix 표현은 space $\mathcal{B}$와 $T$를 곱한 것으로 나타낼 수 있다.

$$
T(\vec{x}) =
\begin{bmatrix}
x_{1} & x_{2} & \dots & x_{m}
\end{bmatrix}
\begin{bmatrix}
a_{1,1} & a_{1,2} & \dots  & a_{1,n} \\
a_{2,1} & a_{2,2} & \dots  & a_{2,n} \\
\vdots  & \vdots  & \ddots & \vdots  \\
a_{m,1} & a_{m,2} & \dots  & a_{m,n}
\end{bmatrix}
$$

1. 두 linear mapping의 composition을 matrix로 표현할 때는 각 mapping들의 matrix 표현을 연속해서 나타낸다.  
Linear space $\mathcal{A}, \mathcal{B}, \mathcal{C}$와 이에 대한 linear mapping $T: \mathcal{A} \rightarrow \mathcal{B}$, $S: \mathcal{B} \rightarrow \mathcal{C}$를 가정해보자.  
$T$와 $S$의 composition인 linear mapping $R: \mathcal{A} \rightarrow \mathcal{C}$는 아래와 같이 표현할 수 있다.

$$
S(T(\vec{v})) = \vec{v} TS
$$

## Cramer의 법칙

