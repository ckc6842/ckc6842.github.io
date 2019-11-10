---
title: "Euclidean Space"
categories:
  - Computer Graphics
tags:
  - Linear Algebra
MathJax: true
---

## Inner Product Space
$\mathcal{V}$가 $\mathbb{R}^{n}$에 대한 vector space라고 하자.  
$\mathcal{V}^{2}$는 $\vec{u},\vec{v} \in \mathcal{V}$의 모든 쌍 $(\vec{u},\vec{v})$의 집합을 나타낸다고 하자.  
이때 *inner product*는 $\mathcal{V}^{2}$로부터 $\mathbb{R}$으로의 function이고, $\langle \vec{u}, \vec{v} \rangle$로 나타낸다.  
Inner product는 아래와 같은 조건을 만족한다.  
1. 분배법칙: $\langle a_{1}\vec{u_{1}} + a_{2}\vec{u_{2}}, \vec{v} \rangle = a_{1}\langle \vec{u_{1}}, \vec{v} \rangle + a_{2}\langle \vec{u_{2}}, \vec{v} \rangle$
2. 교환법칙: $\langle \vec{u}, \vec{v} \rangle = \langle \vec{v}, \vec{u} \rangle$
3. Positive definiteness: $\langle \vec{u}, \vec{u} \rangle \ge 0$이고 $\langle \vec{u}, \vec{u} \rangle = 0$ $\Longleftrightarrow$ $\vec{u} = \vec{0}$

이때 space $\mathcal{V}$는 *inner product* space 이다.

### Norm, Length, Distance
$\mathbb{R}^{n}$의 inner product는 무수히 많으므로, 조건들을 만족하는 쌍에 대한 임의의 function을 특정 지을 수 있다.  
Dot product는 inner product의 한 종류이다.  

Inner product의 세번째 조건은 길이에 대한 정의를 포함한다.  
Inner product의 square root를 *norm*이라고 하고, $||\vec{u}|| = \sqrt{\langle \vec{u}, \vec{u} \rangle}$로 표시한다.
Norm은 euclidean space 상에서 vector의 길이로 해석된다.  

만약 vector의 norm이 1이면 vector가 *normalized* 되었다고 한다.  
$\vec{u} \in \mathcal{V}$인 모든 vector는 $1/||\vec{u}||$를 곱해서 normalize 할 수 있다.  
두 vector $\vec{u}, \vec{v} \in \mathcal{V}$ 사이의 *distance*는 $||\vec{v} - \vec{u}||$로 정의한다.


## Orthogonality and Orthonormal Sets
Euclidean space $\mathcal{V}$에서 $\langle \vec{u}, \vec{v} \rangle = 0$이면, 두 vector는 *orthogonal*하다고 한다.  
Orthogonality는 basis vector의 컨셉과 관련해서 매우 중요하다.  
Vector space $\vec{v}$에 대한 basis vector 집합 $v=\{\vec{v_{1}}, \vec{v_{2}}, \dots, \vec{v_{n}} \}$을 가정해보자.  
$\langle \vec{u}, \vec{v} \rangle = 0$이고 $\forall \vec{v_{i}}, \vec{v_{k}} \in V, i \neq k$이면, 집합 $V$를 *orthogonal set*이라 부른다.  
더 나아가서 $V$가 orthogonal set이고 $||\vec{v_{i}}|| = 1, \forall \vec{v_{i}} \in V$이면, $V$는 *orthonormal*이라고 부른다.  
표준적인 orthonormal frame이 있는 euclidean space를 *Cartesian* sapce라고 부른다.

모든 euclidean space는 space를 정의하는 무한한 수의 basis vector의 집합을 갖는다.  
이 중 어떤 집합은 orthogonal 할 수도, orthonormal할 수도, 혹은 둘 다 아닐 수도 있다.  
하지만 어떤 집합이더라도 *Gram-Schmidt orthogonalization* process를 통해 orthonormal로 바꿀 수 있다.  

$V' = \{ \vec{v_{1}}, \vec{v_{2}}, \dots, \vec{v_{k}} \}, k < n$ (dimension of $\mathcal{V}$)인 vector 집합의 orthonormal set은 basis vector 집합의 부분 집합이므로, 반드시 linearly independent 해야 한다.  
더 나아가 모든 $\vec{u} \in \mathcal{V}$에 대해, vector  

$$
\vec{w} = \vec{u} - \langle \vec{u}, \vec{v_{1}} \rangle\vec{v_{1}} - \langle \vec{u}, \vec{v_{2}} \rangle\vec{v_{2}} - \dots - \langle \vec{u}, \vec{v_{k}} \rangle\vec{v_{k}}
$$

는 각 $\vec{v_{i}} \in V'$와 orthogonal 해야 한다.

$\mathcal{V}$가 inner product space이고 $V = \{ \vec{v_{1}}, \vec{v_{2}}, \dots, \vec{v_{n}} \}$이 basis라고 가정해보자.  
Gram-Schmidt orthogonalization process를 통해 orthonormal basis $U = \{ \vec{u_{1}}, \vec{u_{2}}, \dots, \vec{u_{n}} \}$을 만들 수 있다.

Step 1. $\vec{u_{1}} = \frac{\vec{v_{1}}}{||\vec{v_{1}}||}$을 설정한다. $\vec{u_{1}}$은 unit length가 된다.  
Step 2. $\vec{u_{2}} = \frac{\vec{v_{2}} - \langle \vec{v_{2}}, \vec{u_{1}} \rangle\vec{u_{1}}}{||\vec{v_{2}} - \langle \vec{v_{2}}, \vec{u_{1}} \rangle\vec{u_{1}}||}$을 설정한다. $\vec{u_{2}}$도 unit length이고 $\vec{u_{1}}$과 orthogonal 하다. 집합 $\{ \vec{u_{1}}, \vec{u_{2}} \}$는 orthonormal이다.  
Step 3. $\vec{v_{3}} = \frac{\vec{v_{3}} - \langle \vec{v_{3}}, \vec{u_{1}} \rangle\vec{u_{1}} - \langle \vec{v_{3}}, \vec{u_{2}} \rangle}{||\vec{v_{3}} - \langle \vec{v_{3}}, \vec{u_{1}} \rangle\vec{u_{1}} - \langle \vec{v_{3}}, \vec{u_{2}} \rangle||}$을 설정한다. $\vec{u_{3}}$도 unit length이고 $\vec{u_{1}}, \vec{u_{2}}$와 orthogonal 하다. 집합 $\{ \vec{u_{1}}, \vec{u_{2}}, \vec{u_{3}} \}$는 orthonormal이다.  
Step 4. 위 과정을 모든 $\vec{u_{i}}$에 대해 반복한다.