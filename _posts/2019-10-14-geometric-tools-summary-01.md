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
{% include graph.html name="graph1" width=200 height=200 float="left" %}
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

{% include graph.html name="graph2" width=200 height=200 float="left" %}
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

{% include graph.html name="graph3" width=200 height=200 float="left" %}
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