---
title: "Linear System"
categories:
  - Computer Graphics
tags:
  - Linear Algebra
d3: true
MathJax: true
---

## Linear Equations
Linear equation은 각 항이 linear거나 constant인 방정식이다.
여기서 linear는 실수와 변수의 곱으로 나타나는 항을 뜻한다.

$ 5x + 3 = 7 $  
$ 2x_{1} + 4 = 12 + 17x_{2} - 5x_{3} $

수학적으로 표기할 때는 한 변에는 변수와 관련된 모든 항을, 다른 변에는 constant를 정리한다.

$ 5x = 4 $  
$ 2x_{1} - 12x_{2} = 8 $

이에 대한 표준형은 다음과 같다.

$ ax = c $  
$ a_{1}x_{1} + a_{2}x_{2} = c $  
$ a_{1}x_{1} + a_{2}x_{2} + ... + a_{n}x_{n} = c $

위의 표준형에서 $a$는 계수(coefficients), $x$는 미지수라고 부른다.

두 개의 미지수 $x, y$를 가진 linear equation은 일반적으로 2차원 데카르트 좌표계 상에서 직선으로 나타낼 수 있다.

## Linear Systems in Two Unknowns
### Linear system
둘 이상의 linear equation의 집합을 뜻한다.

두 개의 미지수를 가진 두 개의 equation을 가정해보자.  
상기 언급한 바와 같이 두 개의 미지수를 가진 linear equation은 2차원 공간에서 직선으로 표현할 수 있다.  
그럼, 각 equation을 2차원 공간에 나타낸 두 개의 직선 대해 다음과 같은 상황들이 존재한다.

1. 두 직선이 한 점에서 교차함
2. 두 직선이 만나지 않음 (평행함)
3. 두 직선이 겹침

{% include initialize-graph %}
{% include graph.html name="graph1" width=200 height=200 %}
<script>
var graphObj = graph['graph1']
var line1 = graphObj['svg'].append('g')
line1.append('line')
  .attr('x1', graphObj['xScale'](-0.3))
  .attr('y1', graphObj['yScale'](1))
  .attr('x2', graphObj['xScale'](0.67))
  .attr('y2', graphObj['yScale'](-1))
  .style('stroke', 'red')
line1.append('text')
  .attr('text-anchor', 'middle')
  .attr('x', graphObj['xScale'](-0.3))
  .attr('y', graphObj['yScale'](1))
  .style('font-size', '14px')
  .style('font-weight', 'bold')
  .text('3x + 2y = 6')

var line2 = graphObj['svg'].append('g')
line2.append('line')
  .attr('x1', graphObj['xScale'](1))
  .attr('y1', graphObj['yScale'](0))
  .attr('x2', graphObj['xScale'](0))
  .attr('y2', graphObj['yScale'](-1))
  .style('stroke', 'red')
line2.append('text')
  .attr('text-anchor', 'middle')
  .attr('x', graphObj['xScale'](0.85))
  .attr('y', graphObj['yScale'](0.03))
  .style('font-size', '14px')
  .style('font-weight', 'bold')
  .text('x - y = 1')
</script>

{% include graph.html name="graph2" width=200 height=200 %}
<script>
var graphObj = graph['graph2']
var line1 = graphObj['svg'].append('g')
line1.append('line')
  .attr('x1', graphObj['xScale'](-0.3))
  .attr('y1', graphObj['yScale'](1))
  .attr('x2', graphObj['xScale'](0.67))
  .attr('y2', graphObj['yScale'](-1))
  .style('stroke', 'red')
line1.append('text')
  .attr('text-anchor', 'middle')
  .attr('x', graphObj['xScale'](-0.65))
  .attr('y', graphObj['yScale'](1))
  .style('font-size', '14px')
  .style('font-weight', 'bold')
  .text('3x + 2y = 6')

var line2 = graphObj['svg'].append('g')
line2.append('line')
  .attr('x1', graphObj['xScale'](0))
  .attr('y1', graphObj['yScale'](1))
  .attr('x2', graphObj['xScale'](0.97))
  .attr('y2', graphObj['yScale'](-1))
  .style('stroke', 'red')
line2.append('text')
  .attr('text-anchor', 'middle')
  .attr('x', graphObj['xScale'](0.35))
  .attr('y', graphObj['yScale'](1))
  .style('font-size', '14px')
  .style('font-weight', 'bold')
  .text('6x + 4y = 24')
</script>

{% include graph.html name="graph3" width=200 height=200 %}
<script>
var graphObj = graph['graph3']
var line1 = graphObj['svg'].append('g')
line1.append('line')
  .attr('x1', graphObj['xScale'](-0.3))
  .attr('y1', graphObj['yScale'](1))
  .attr('x2', graphObj['xScale'](0.67))
  .attr('y2', graphObj['yScale'](-1))
  .style('stroke', 'red')
line1.append('text')
  .attr('text-anchor', 'middle')
  .attr('x', graphObj['xScale'](-0.6))
  .attr('y', graphObj['yScale'](0.7))
  .style('font-size', '14px')
  .style('font-weight', 'bold')
  .text('3x + 2y = 6')

var line2 = graphObj['svg'].append('g')
line2.append('line')
  .attr('x1', graphObj['xScale'](-0.3))
  .attr('y1', graphObj['yScale'](1))
  .attr('x2', graphObj['xScale'](0.67))
  .attr('y2', graphObj['yScale'](-1))
  .style('stroke', 'red')
line2.append('text')
  .attr('text-anchor', 'middle')
  .attr('x', graphObj['xScale'](0.2))
  .attr('y', graphObj['yScale'](0.9))
  .style('font-size', '14px')
  .style('font-weight', 'bold')
  .text('6x + 4y = 12')
</script>
{% include end-graph %}
위 그래프 중 첫번째는 $ u = (k_{1}, k_{2}) $ 인 점이 두 equation의 공통된 해가 된다.  

한편 두번째와 세번째 그래프는 두 linear equation의 계수들이 비례 관계 ($ \frac{a_{1,1}}{a_{2,1}} = \frac{a_{1,2}}{a_{2,2}} $)이다.  
두 그래프의 차이점은 constant항의 비례 관계인지 여부에 따라 발생한다.  
두번째 그래프는 constant 항은 비례 관계가 아니어서 두 직선이 평행하게 배치된다. 따라서 두 equation의 해는 존재하지 않는다.  
반면 세번째 그래프는 constant 항이 비례 관계여서 두 직선이 겹친다. 따라서 두 equation은 무수히 많은 해를 갖게 된다.  

만약 두 linear equation에서 해가 존재한다면 elimination 과정을 거쳐 해를 구할 수 있다.  

## Matrix Form of General Linear System
$m \times n$ linear system의 표준형은

$$
\begin{array}a 
a_{1,1}x_{1} + a_{1,2}x_{2} + \dots + a_{1,n}x_{n} & = & c_{1} \\
a_{2,1}x_{1} + a_{2,2}x_{2} + \dots + a_{2,n}x_{n} & = & c_{2} \\
& \vdots & \\
a_{m,1}x_{1} + a_{m,2}x_{2} + \dots + a_{m,n}x_{n} & = & c_{m}
\end{array}
$$

로 나타낼 수 있다.  
여기서 $c_{1} = c_{2} = \dots = c_{m} = 0$인 system을 **homogeneous** system이라고 한다.

위 linear system의 표준형을 matrix $AX = C$ 형태로 나타내면 다음과 같다.

$$
\begin{bmatrix}
a_{1,1} & a_{1,2} & \dots & a_{1,n} \\
a_{2,1} & a_{2,2} & \dots & a_{2,n} \\
        &         & \vdots &        \\
a_{m,1} & a_{m,2} & \dots & a_{m,n}
\end{bmatrix}
\begin{bmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_{n}
\end{bmatrix}
=
\begin{bmatrix}
c_{1} \\
c_{2} \\
\vdots \\
c_{n}
\end{bmatrix}
$$

여기서 계수만 모아 놓은 matrix A를 **coefficient* matrix라고 한다.  
그리고, 

$$
\begin{bmatrix}
a_{1,1} & a_{1,2} & \dots & a_{1,n} & c_{1} \\
a_{2,1} & a_{2,2} & \dots & a_{2,n} & c_{2} \\
        &         & \vdots &        &       \\
a_{m,1} & a_{m,2} & \dots & a_{m,n} & c_{m}
\end{bmatrix}
$$

위와 같이 계수와 constant만 나열한 matrix를 **augmented** matrix라 한다.  
이렇게 matrix 형태로 나타낸 linear system의 해를 구하는 방법은 다양한데, 가장 흔히 사용하는 방법 중 하나는 *Gaussian elimination*이다.

## Row Reduction, Echelon Form, Rank
Augmented matrix 형태에서 linear system의 해를 구하는 과정은 다음과 같다.

$$
\begin{bmatrix}
3 & 2 & 6 \\
1 & -1 & 1
\end{bmatrix}
$$

위 matrix에서 두번째 행에 -3을 곱해서 각 linear equation의 첫번째 계수의 크기를 맞추면 다음과 같은 matrix가 나온다.

$$
\begin{bmatrix}
3 & 2 & 6 \\
-3 & 3 & -3
\end{bmatrix}
$$

여기서 두 equation을 더한 후, 그 결과를 두번째 행과 대체하면 다음과 같은 matrix가 나온다.

$$
\begin{bmatrix}
3 & 2 & 6 \\
0 & 1 & \frac{3}{5}
\end{bmatrix}
$$

이 결과로 두번째 미지수에 대한 해 $\frac{3}{5}$를 바로 구할 수 있다.  
여기서 주목해야 하는 점은 마지막 행의 첫번째 열의 값이 0이라는 점이다.

위와 같은 과정을 linear system의 표준형 matrix에 적용하면 다음과 같은 결과를 얻을 수 있다.

$$
\begin{bmatrix}
b_{1,1} & b_{1,2}     & b_{1,3}     & \dots  & b_{1,n} & d_{1} \\
        & b_{2,k_{2}} & b_{2,k{3}}  & \dots  & b_{2,n} & d_{2} \\
        &             &             & \vdots &         &       \\
        &             & b_{r,k_{r}} & \dots  & b_{r,n} & d_{r}
\end{bmatrix}
$$

여기서 마지막 행은 $m$이 아닌, $r <= m$인 $r$로 표현된다.  
그 이유는 상기 과정을 거치며 일부 equation은 제거될 수 있기 때문이다.  
위와 같은 과정 중에 $0x_{1} + 0x_{2} + \dots + 0x_{n} = c_{i}$와 같은 equation이 나타날 수 있다.  
여기서 $c_{i} = 0$이면 equation이 완벽하게 제거되므로 결과에 영향을 미치지 않는다.  
반면 $c_{i} \neq 0$이면 system의 해가 존재하지 않는 상황이므로 계산을 멈출 수 있다.  
한편 r과 n의 관계도 중요한데, $r = n$이면 system은 유일한 해를 가지고, $r < n$이면 미지수가 equation보다 많으므로 다수의 해가 존재한다.

위에서 본 연산 과정은 아래과 같은 순서로 정리할 수 있다.
- 두 행의 순서를 바꾼다.
- 두 행의 계수를 맞춰준다. (한 행에 0이 아닌 수를 곱한다)
- 두 행의 합을 한 행과 대체한다.
이 연산의 과정을 *row reduction*이라 한다.  
그리고 row reduction을 반복하여 더 이상 reduction 할 수 없는 상태의 matrix, 즉 row reduction의 결과를 echelon form이라 한다.






