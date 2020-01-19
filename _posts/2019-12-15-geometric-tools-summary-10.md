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

오른손 법칙에 따라서

$$
sgn(\vec{u}, \vec{v}, \vec{w}) = sgn(\vec{u}, \vec{v}, \vec{w}_{||})= 
\begin{cases}
  +1 & \Longleftrightarrow \vec{w}_{||} || \vec{u}\times\vec{v} \\
  -1 & \Longleftrightarrow \vec{w}_{||} || -\vec{u}\times\vec{v} \\
\end{cases}
$$

이므로 수식은 다음과 같이 정리할 수 있다.

$$
Vol(\vec{u}, \vec{v}, \vec{w}) = sgn(\vec{u}, \vec{v}, \vec{w})((\vec{u}\times\vec{v})\cdot\vec{w})
$$

여기서 $(\vec{u}\times\vec{v})\cdot\vec{w}$는 보통 *scalar triple product*라고 부르고, 이는 $\vec{u}, \vec{v}, \vec{w}$가 순서대로 행/열로 나열된 matrix의 determinant이다.

$$
det(\vec{u}, \vec{v}, \vec{w})
$$

즉, 정리된 수식에 대입하면 부피는 *signed* determinant라고 할 수 있다.

$$
Vol(\vec{u}, \vec{v}, \vec{w}) = |det(\vec{u}, \vec{v}, \vec{w})| = sgn(\vec{u}, \vec{v}, \vec{w})det(\vec{u}, \vec{v}, \vec{w})
$$

Determinent, scalar triple product, 부피와 관련된 또다른 속성들은 다음과 같다.
1. Determinant $det(\vec{u}, \vec{v}, \vec{w})$는 집합 $\{\vec{u}, \vec{v}, \vec{w}\}$이 basis를 이룰때만 0이 아니다.
   예를 들어 3차원 공간에서 세 vector가 basis를 이루지 않으면, 세 vector는 부피가 없는 면이나 선을 span한다.
2. Determinant $det(\vec{u}, \vec{v}, \vec{w})$는 $(\vec{u}, \vec{v}, \vec{w})$의 sign이 0보다 클 때만 양수이다.
3. Vector 간의 순환하는 순서 변경은 determinant 값에 영향이 없다.
   $det(\vec{u}, \vec{v}, \vec{w}) = det(\vec{w}, \vec{u}, \vec{v}) = det(\vec{v}, \vec{w}, \vec{u})$
4. Vector 간의 순서가 뒤집어지면 determinant의 부호가 바뀌지만 크기는 변함이 없다.
   $det(\vec{u}, \vec{v}, \vec{w}) = -det(\vec{w}, \vec{v}, \vec{u}) = -det(\vec{v}, \vec{u}, \vec{w}) = -det(\vec{u}, \vec{w}, \vec{v})$
5. 한 vector의 부호가 뒤집어지면 determinant의 부호가 바뀐다.
   $det(\vec{u}, \vec{v}, \vec{w}) = -det(-\vec{u}, \vec{v}, \vec{w}) = -det(\vec{u}, -\vec{v}, \vec{w}) = -det(\vec{u}, \vec{v}, -\vec{w})$
6. 한 vector에 scalar 곱을 하면 determinant도 그만큼 커진다.
   $det(c\vec{u}, \vec{v}, \vec{w}) = det(\vec{u}, c\vec{v}, \vec{w}) = det(\vec{u}, \vec{v}, c\vec{w}) = c det(\vec{u}, \vec{v}, \vec{w})$
7. 오른손 basis vector들의 orthonormal space는 unit determinant를 갖는다.


## Frames
Point들의 집합 $\mathcal{P}$와 $n$차원의 vector space $\mathcal{V}$로 정의되는 affine space $\mathcal{A}$에 대해서,  
임의의 point $\mathcal{O} \in \mathcal{P}$와 basis $$\vec{v}_{1}, \vec{v}_{2}, \dots, \vec{v}_{n} \in \mathcal{V}$$ 를 선택했을 때,  
이는 $\mathcal{A}$에 대한 $frame^{2}$을 형성한다.  
Frame은 아래와 같이 표기한다.

$$
\mathcal{F} = (\vec{v}_{1}, \vec{v}_{2}, \dots, \vec{v}_{n}, \mathcal{O})^{T}
$$

Vector sapce $\mathcal{V}$에서는 해당 space에 포함되어 있는 어떤 vector $\vec{u}$ 도 basis vector들의 집합의 linear comination으로 나타낼 수 있다.

$$
\vec{u} = a_{1}\vec{v}_{1} + a_{2}\vec{v}_{2} + \cdots + a_{n}\vec{v}_{n}
$$

여기서 $a_{1}, a_{2}, \dots, a_{n}$은 $\vec{u}$의 *coordinates*이며 basis $\vec{v}_{1}, \vec{v}_{2}, \dots, \vec{v}_{n}$과 관계가 있다.

그렇다면 $\mathcal{P}$의 point들에 대해서는 어떨까?  
Point $\mathcal{P}$와 vector $\vec{u}$가 있을 때, $\mathcal{Q} = \mathcal{P} + \vec{u}$인 유일한 point가 존재한다.  
만약 $\mathcal{F}$에서 point $\mathcal{O}$를 $\mathcal{P}$로 고르면, point $\mathcal{Q} \in \mathcal{P}$는 특정 vector $\vec{u}$를 $\mathcal{O}$와 더한 것으로 정의할 수 있다.

$$
\begin{array}a
\mathcal{Q} & = & \vec{u} + \mathcal{O} \\
            & = & a_{1}\vec{v}_{1} + a_{2}\vec{v}_{2} + \cdots + a_{n}\vec{v}_{n} + \mathcal{O}
\end{array}
$$

마찬가지로 $\mathcal{Q}$의 coordinates들은 $a_{1}, a_{2}, \dots, a_{n}$이다.

### 데카르트 좌표계의 Frames

모든 vector $\vec{v}$는 *unit vector* $\hat{v}$ 와 관계가 있다.  
Unit vector는 $\vec{v}$와 방향은 같지만, 길이가 1인 vector이다.  
즉, unit vector는 $\vec{v}$를 그 길이로 나누면 구할 수 있다.

$$
\hat{v} = \frac{\vec{v}}{||\vec{v}||}
$$

이를 통해 basis vector들이 

## Affine Transformations
*Affine transformation*은 어떤 affine space에 있는 point들과 vector들을 다른 affine space로 mapping 하는 것을 말한다.
일반적으로, $T: \mathcal{A}^{n} \mapsto \mathcal{B}^{m}$가 affine transformation이려면, affine combination을 유지하고, $P_{i} \in \mathcal{A}$와 $\sum_{i=1}^{n}a_{1} = 1$을 만족해야 한다.

$$
T(a_{1}P_{1} + a_{2}P_{2} + \cdots + a_{n}P_{n}) = a_{1}T(P_{1}) + a_{2}T(P_{2}) + \cdots + a_{n}T(P_{n})
$$

주의해야 할 점은 차원 n과 m은 꼭 같을 필요는 없지만, $m \leq n$이 성립해야 한다.  
그 이유는 affine transformation이 geometric object들을 대응되는 object들에 mapping하기 때문이다.

앞서 affine combination에 대한 내용에서 point $R$을 같은 line 상에 있는 point $P$와 $Q$의 affine combination으로 나타내는 것을 보았다.

$$
R = (1 - \alpha)P + \alpha Q
$$

여기에 affine tranformation을 적용하면 다음과 같다.

$$
\begin{array}a
T(R) & = & T((1 - \alpha)P + \alpha Q)\\
     & = & (1 - \alpha)T(P) + \alpha T(Q)
\end{array}
$$

이는 아래와 같이 line의 equation을 $t$에 대한 parametric equation으로 작성한 것과 매우 유사하다.

$$
R(t) = (1 - t)P + tQ
$$

상기 수식에 T를 적용하면 다음과 같다.

$$
\begin{array}a
T(R(t)) & = & T((1 - t)P + tQ) \\
        & = & (1 - t)T(P) + tT(Q)
\end{array}
$$

즉, line의 parametric equation은 $P$와 $Q$에 의해 정의된다.  
위 과정에서 상수($t, 1 - t$)들이 transformation T의 영향을 받지 않은 점이 중요한 점이다.  
이를 affine transformation은 *relative ratios*를 *preserve*한다고 말한다.

Affine space는 point들의 집합과 vector들의 집합으로 구성되어 있기 때문에, affine transformation이 vector에 미치는 영향도 보아야 한다.  
앞서 본 바대로, 주어진 affine space $\mathcal{A}$와 두 point $P, Q \in \mathcal{A}$에 대해 다음과 같이 vector을 구할 수 있다.

$$
\vec{v} = Q - P
$$

여기에 affine transformation $T$를 적용하면 다음과 같다.

$$
\begin{array}a
T(\vec{v}) & = & T(Q - P) \\
           & = & T(Q) - T(P)
\end{array}
$$

따라서 tranform이 적용된 vector는, transform이 적용된 point들의 차와 같다.  
하지만 affine space에 기초를 둔 vector들은 vector space 내에 존재하는 element이므로, vector의 *location*은 의미가 없다.  
즉, $T(\mathcal{A})$에 또다른 point 쌍을 적용하면, $T(\vec{v})$ 방향과 크기가 같지만 위치가 다른 무수히 많은 복사본을 구할 수 있다.

하지만 affine transformation은 *parallelism*을 *preserve* 한다.  
이를 확인하기 위해 두개의 point 쌍인 {$P_{1}, P_{2}$}와 {$Q_{1}, Q_{2}$}를 가정해보자.  
두 쌍은 각각 아래와 같은 line을 정의한다.

$$
\begin{array}a
\mathcal{L}_{1} & = & P_{1} + \alpha(P_{2} - P_{1}) \\
\mathcal{L}_{2} & = & Q_{1} + \beta(Q_{2} - Q_{1})
\end{array}
$$

이 선들은 $P_{2} - P_{1} = \gamma(Q_{2} - Q_{1})$이면, 다시 말해 두 vector의 방향은 같고 오직 길이가 relative ratio $\gamma$ 만큼의 차이만 있으면 평행이다.  
그렇다면 affine transformation은 동일한 vector를 상기 두 vector로 scale한 것이고, 따라서 affine transformation은 parallelism을 preserve 한다.

위에서 살펴본 내용과 아래 정리된 내용을 활용해 affine tranformation의 특성을 살펴보자.  
Affine transformation $T$는 affine space $\mathcal{A}$의 vector들의 linear transformation이다.
이전에 살펴본 바와 같이 linear transformation은 linear combination을 preserve 한다.
Vector들의 linear combination은 linearly independent한 vector $\vec{v}_{i} \in \mathcal{V}$ 집합에 대해 아래와 같이 정의한다.

$$
\vec{w} = x_{1}\vec{v}_{1} + x_{2}\vec{v}_{2} + \cdots + x_{n}\vec{v}_{n}, x_{i} \in \mathbb{R}
$$

Linear transformation이 linear combination을 preserve 하기 위해서는 $\forall x_{1}, x_{2}, \cdots, x_{n} \in \mathbb{R}, \forall \vec{v}_{1}, \vec{v}_{2}, \cdots, \vec{v}_{n} \in \mathcal{V}$에 대해 아래 식을 만족해야 한다.

$$
\begin{array}a
T(\vec{w}) & = & T(x_{1}\vec{v}_{1} + x_{2}\vec{v}_{2} + \cdots + x_{n}\vec{v}_{n}) \\
           & = & T(x_{1}\vec{v}_{1}) + T(x_{2}\vec{v}_{2}) + \cdots + T(x_{n}\vec{v}_{n}) \\
           & = & x_{1}T(\vec{v}_{1}) + x_{2}T(\vec{v}_{2}) + \cdots + x_{n}T(\vec{v}_{n})
\end{array}
$$

위 식의 전개가 성립하는 것을 증명하기 위해서 2차원 affine space에서의 basis vector들의 덧셈 연산을 통해 차원이 확장 되는지 확인하자.

첫째로,

$$
T(\vec{u} + \vec{v}) = T(\vec{u}) + T(\vec{v})
$$

가 성립함을 보이기 위해 이를 point로 나타내보자.  
$\vec{u} = Q - P$, $\vec{v} = R - Q$일 때 위 식은 다음과 같이 정리된다.

$$
\begin{array}a
T(\vec{u} + \vec{v}) & = & T(R - P) \\
                     & = & T(R) + (T(Q) - T(Q)) - T(P) \\
                     & = & (T(R) - T(Q)) + (T(Q) - T(P)) \\
                     & = & T(\vec{v}) + T(\vec{u}) \\
                     & = & T(\vec{u}) + T(\vec{v}) \\
\end{array}
$$

둘째로,

$$
T(\alpha\vec{v}) = \alpha T(\vec{v})
$$

가 성립함을 보여야 한다.  
이 역시 $\vec{v} = Q - P$가 성립하는 point P, Q를 활용해 표현할 수 있다.  
$\vec{v}$를 $\alpha, 1 - \alpha$로 분할하는 point R이 있을 때, $\alpha\vec{v} = ((1 - \alpha)P + \alpha Q) - P$로 나타낼 수 있다.
이를 토대로 위 식을 전개하면 다음과 같다.

$$
\begin{array}a
T(\alpha\vec{v}) & = & T(((1 - \alpha)P + \alpha Q) - P)  \\
                 & = & T((1 - \alpha)P + \alpha Q) - T(P) \\
                 & = & (1 - \alpha)T(P) + \alpha T(Q) - T(P) \\
                 & = & \alpha T(\vec{v})
\end{array}
$$

마지막으로, affine transformation가 point에 vector를 더한 것을 preserve 하는 것을 보여야 한다.

$$
T(P + \vec{v}) = T(P) + T(\vec{v})
$$

Point와 vector의 합은 $Q = P + \vec{v}, \vec{v} = Q - P$로 나타낼 수 있다.  
이를 통해 식을 전개하면 다음과 같다.

$$
\begin{array}a
T(P + \vec{v}) & = & T(P + (Q - P)) \\
               & = & T(P) + T(Q) - T(P) \\
               & = & T(P) + (T(Q) - T(P)) \\
               & = & T(P) + T(\vec{v})
\end{array}
$$

앞서 본 세 속성은 affine transformation $T$가 affine coordinate를 preserve 하는 것을 증명한다.

$$
T(\alpha_{1}\vec{v}_{1} + \alpha_{2}\vec{v}_{2} + \cdots + \alpha_{n}\vec{v}_{n} + \mathcal{O}) = \alpha_{1}T(\vec{v}_{1}) + \alpha_{2}T(\vec{v}_{2}) + \cdots + \alpha_{n}T(\vec{v}_{n}) + T(\mathcal{O})
$$

### Types of Affine Maps

앞서 본 것과 같이 affine space $\mathcal{A}$ 내 vector 간의 affine transformation 연산은 linear transformation이다.  
이에는 rotation과 scale이 적용된다. 왜냐하면 vector들은 position 정보가 없고, 이는 position과 연관된 translation과 같은 모든 연산을 배제한다.

Affine transformation이 $\mathcal{A}.\mathcal{P}$와 $\mathcal{A}.\mathcal{V}$에 적용되면, relative postion을 포함한 transformation을 표현할 수 있다.
* Translations
* 임의의 line이나 plane에 대한 mirror or reflection
* Parallel projection
* 임의의 point에 대한 rotation
* 임의의 line이나 plane과 연관된 shearing



## Barycentric Coordinates and Simplexes
앞서 살펴본 것과 같이 affine space는 vector space를 기반으로 한 basis vector들과 point로 정의할 수 있다.

$$
\begin{array}a
\mathcal{Q} & = & \vec{u} + \mathcal{O} \\
            & = & a_{1}\vec{v}_{1} + a_{2}\vec{v}_{2} + \cdots + a_{n}\vec{v}_{n} + \mathcal{O}
\end{array}
$$

이에 대한 다른 대안은 basis point를 사용하는 것이다.  
이는 basis vector들을 point $\mathcal{O}$와 더해서 얻은 point의 집합으로 구성한다.
($$P_{0} = \mathcal{O}, P_{1} = \mathcal{O} + \vec{v}_{1}, P_{2} = \mathcal{O} + \vec{v}_{2}, \cdots, P_{n} = \mathcal{O} + \vec{v}_{n}$$)

이를 통해 $\mathcal{Q} \in \mathcal{A}$인 point를 정리하면 다음과 같다.

$$
\mathcal{Q} = \mathcal{P}_{0}(1 - a_{1} - a_{2} - \cdots - a_{n}) + P_{1}a_{1} + P_{2}a_{2} + \cdots + P_{n}a_{n}
$$

또는 아래와 같이 정리할 수 있다.

$$
Q = P_{0}a_{0} + P_{1}a_{1} + \cdots + P_{n}a_{n}
$$

위의 식에서 $1 = a_{0} + a_{1} + \cdots + a_{n}$, 다시 말해 모든 계수의 합은 1이어야 한다.

### Barycentric Coordinates and Subspaces

### Affine Independence

