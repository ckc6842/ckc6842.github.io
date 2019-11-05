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

그리고 $a \mapsto U(T(a))$

### Mapping의 특별한 종류


### Inverse Mappings


## Linear Mappings


## Linear Mappings의 Matrix 표현


## Cramer의 법칙

