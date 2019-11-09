---
title: "Eigenvalues and Eigenvectors"
categories:
  - Computer Graphics
tags:
  - Linear Algebra
MathJax: true
---

$n \times 1$과 $1 \times n$ matrix는 vetor이다.  
vector는 space 내에서 방향이나 거리를 나타내므로, matrix를 vector로 곱하는 것은 vector의 방향이나 길이로 transform을 하는 것으로 볼 수 있다.  
이러한 vector 곱셈은 다음과 같이 표현할 수 있다.

$$
\vec{v}' = \vec{v}M
$$

일부 특별한 vector $\vec{v}$에 대해 다음과 같은 식이 성립하는 constant $\lambda$를 구할 수 있다.

$$
\vec{v}' = \lambda\vec{v}
$$

이를 첫 번째 식에 대입하면 다음과 같이 정리할 수 있다.

$$
\vec{v}M = \lambda\vec{v}
$$

위와 같이 $\lambda$를 구할 수 있는 vector $\vec{v}$를 matrix $M$의 *eigenvector*라고 하고, $\lambda$는 *eigenvalue*라고 한다.  
$\lambda$는 scalar 값이므로 $\lambda\vec{v}$는 $\vec{v}$의 scaled 된 형태라고 볼 수 있고, 따라서 $\vec{v}$에 $M$을 곱하는 것은 단순히 eigenvector를 scale하는 것이다,

### Eigenvalue의 계산
위의 식을 변형하면 다음과 같은 식이 도출된다.

$$
\vec{v}M = \lambda\vec{v} \\
\vec{v}(\lambda I - M) = \vec{0}
$$

$\vec{v}$가 $\vec{0}$ vector가 아니면,

$$
|\lambda I - M| = 0
$$

*characteristic polynomial*이라고 부르는 위 식이 성립해야 한다.  
즉, 위 식을 풀면 eigenvalue $\lambda$의 값을 구할 수 있다.

