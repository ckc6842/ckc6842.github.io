---
title: "Least Squares"
categories:
  - Computer Graphics
tags:
  - Linear Algebra
MathJax: true
d3: true
---

두 개의 점  

$$
P_{1} = (p_{1,1}, p_{1,2}) \\
P_{2} = (p_{2,1}, p_{2,2})
$$

이 있을 때, 두 점을 지나는 직선의 방정식 $x_{2} = mx_{1} + b$를 정의할 수 있다.  
이를 아래와 같은 linear system으로 나타낼 수 있다.

$$
p_{1,1}m + b = p_{1,2} \\
p_{2,1}m + b = p_{2,2}
$$

그리고 matrix form으로 나타내면 다음과 같다.

$$
\begin{bmatrix}
p_{1,1} & 1 \\
p_{2,1} & 1
\end{bmatrix}
\begin{bmatrix}
m \\
b
\end{bmatrix}
=
\begin{bmatrix}
p_{1,2} \\
p_{2,2}
\end{bmatrix}
$$

이를 Cramer의 법칙을 통해 계산하면 다음과 같다.

$$
m = 
\frac{
  \begin{vmatrix}
  p_{1,2} & 1 \\
  p_{2,2} & 1
  \end{vmatrix}
}{
  \begin{vmatrix}
  p_{1,1} & 1 \\
  p_{2,1} & 1
  \end{vmatrix}
}
=
\frac{
  p_{1,2} - p_{2,2}
}{
  p_{1,1} - p_{2,1}
}
$$

$$
b = 
\frac{
  \begin{vmatrix}
  p_{1,1} & p_{1,2} \\
  p_{2,1} & p_{2,2}
  \end{vmatrix}
}{
  \begin{vmatrix}
  p_{1,1} & 1 \\
  p_{2,1} & 1
  \end{vmatrix}
}
=
\frac{
  p_{1,1}p_{2,2} - p_{2,1}p_{1,2}
}{
  p_{1,1} - p_{2,1}
}
$$

하지만 점의 개수가 3개 이상이 되면, 하나의 직선 위에 위치하지 못할 수도 있다.  
이런 경우에는 각 점과 직선 사이의 거리를 최소화 하려 할 것이다.  
직선의 방정식을 x 좌표를 대입했을 때 y 좌표를 반환하는 function $f(x) = mx + b$로 가정해보자.  
그럼 점 3개에 대한 linear system은 다음과 같이 정리할 수 있다.  

$$
p_{1,1}m + b = p_{1,2} \\
p_{2,1}m + b = p_{2,2} \\
p_{3,1}m + b = p_{3,2}
$$

또한 matrix form으로 나타내면 다음과 같다.

$$
\begin{bmatrix}
p_{1,1} & 1 \\
p_{2,1} & 1 \\
p_{3,1} & 1
\end{bmatrix}
\begin{bmatrix}
m \\
b
\end{bmatrix}
=
\begin{bmatrix}
p_{1,2} \\
p_{2,2} \\
p_{3,2}
\end{bmatrix}
$$

미지수는 2개이지만 equation은 3개인 상태인데, 이와 같이 미지수보다 equation의 개수가 많은 system을 *overdetermined* system이라 부른다.  
이러한 경우에는 특정 기준을 만족시킬 수 있는 approximate solution을 사용해야 한다.  

{% include initialize-graph %}
{% include graph.html name="graph1" width=400 height=400 %}
<script>
var graphObj = graph['graph1']
var line = graphObj['svg'].append('g')
line.append('line')
  .attr('x1', graphObj['xScale'](-1))
  .attr('y1', graphObj['yScale'](-0.5))
  .attr('x2', graphObj['xScale'](1))
  .attr('y2', graphObj['yScale'](0.5))
  .style('stroke', 'red')

for (var i = 1; i <= 3; i++) {
  var startX = -0.8
  var xBias = (i - 1) * 0.7
  var currentX = startX + xBias
  var currentLabelX = currentX - 0.15

  var startY = -0.4
  var yBias = (i - 1) * 0.35
  var currentOnLineY = startY + yBias
  var currentOriginY = startY + yBias + ((i % 2 === 0) ? 0.4 : -0.4)
  var currentOnLineLabelY = currentOnLineY + ((i % 2 === 0) ? -0.05 : 0.15)
  var currentOriginLabelY = currentOriginY + ((i % 2 === 0) ? 0.15 : -0.05)

  var pointOnLine = graphObj['svg'].append('g')
  pointOnLine.append('circle')
    .attr('cx', graphObj['xScale'](currentX))
    .attr('cy', graphObj['yScale'](currentOnLineY))
    .attr('r', 4)
    .style('fill', 'none')
    .style('stroke', 'red')
  pointOnLine.append('g')
    .attr('class', 'jax')
    .attr('transform', 'translate(' + graphObj['xScale'](currentLabelX) + ',' +    graphObj['yScale'](currentOnLineLabelY) + ')')
    .append('text')
    .text('$(x_{' + i.toString() + '}, mx_{' + i.toString() + '} + b)$')

  var pointOrigin = graphObj['svg'].append('g')
  pointOrigin.append('circle')
    .attr('cx', graphObj['xScale'](currentX))
    .attr('cy', graphObj['yScale'](currentOriginY))
    .attr('r', 4)
    .style('fill', 'red')
  pointOrigin.append('g')
    .attr('class', 'jax')
    .attr('transform', 'translate(' + graphObj['xScale'](currentLabelX) + ',' +    graphObj['yScale'](currentOriginLabelY) + ')')
    .append('text')
    .text('$(x_{' + i.toString() + '}, y_{' + i.toString() + '})$')

  var verticalLine = graphObj['svg'].append('g')
  verticalLine.append('line')
    .attr('x1', graphObj['xScale'](currentX))
    .attr('y1', graphObj['yScale'](currentOnLineY))
    .attr('x2', graphObj['xScale'](currentX))
    .attr('y2', graphObj['yScale'](currentOriginY))
    .style('stroke-dasharray', ('3, 3'))
    .style('stroke', 'red')
}

setTimeout(() => {
  window.MathJax.Hub.Register.StartupHook("End", function() {
    setTimeout(() => {
      graphObj['svg'].selectAll('.jax').each(function(){
        var self = d3.select(this),
            g = self.select('text>span>svg');
        g.remove();
        self.append(function(){
          return g.node();
        });
      });
    }, 1);
  });
  
  window.MathJax.Hub.Queue(["Typeset", MathJax.Hub, graphObj['svg'].node()]);
}, 500);    
</script>
{% include end-graph %}
*<center>Least Square on Cartesian Space</center>*

점 $(x_{1}, y_{1})$과 직선 사이의 y좌표계 상의 거리는 $D_{1} = |f(x_{1}) - y_{1}|$ 이다.  
원래는 거리의 합이 최소가 되는 직선의 방정식을 구해야 하지만, 계산의 편의를 위해 거리의 제곱의 합을 구한다.  

$$
D^{2} = (f(x_{1}) - y_{1})^{2} + (f(x_{2}) - y_{2})^{2} + \dots + (f(x_{n}) - y_{n})^{2}
$$

여기서 $D^{2}$가 최소가 되는 $m$과 $b$의 값을 approximate 해야 한다.  
제곱이 최소가 되는 approximation이므로 *least square* solution이라 부른다.  

$n$이 점의 개수인 $n$차원 space $\mathcal{R}^{n}$을 가정해보자.  
이 때 위 space 내의 위치 $y$의 좌표를 우리가 맞춰야 할 점들의 y 값으로 구성할 수 있다($y = (y_{1}, y_{2}, \dots, y_{n})$).  
이 space 내의 또 다른 위치 $T(f)$는 우리가 맞춰야 할 점들이 approximation 후에 직선 상에 놓인 점들의 y 값으로 구성할 수 있다($T(f) = (f(x_{1}), (f(x_{2}), \dots, (f(x_{n}))$).  
따라서 총 거리의 합 $D^{2}$는 vector $T(f) - y$의 거리의 제곱이다.  

세 점을 맞출 때의 transformation $T$는 다음 행렬과 같다.  

$$
M =
\begin{bmatrix}
1 & x_{1} \\
1 & x_{2} \\
1 & x_{3}
\end{bmatrix}
$$

여기서, $D^{2}$ 가 최소가 되는 $f$, 즉 $m, b$를 구해야 한다.  
위의 $M$을 이용해 행렬식으로 나타내면 다음과 같다.  

$$
\begin{align}
M\begin{bmatrix}
f
\end{bmatrix} -
\begin{bmatrix}
y
\end{bmatrix}
 & =
M\begin{bmatrix}
b \\
m
\end{bmatrix} -
\begin{bmatrix}
y
\end{bmatrix} \\

 & =
\begin{bmatrix}
1 & x_{1} \\
1 & x_{2} \\
1 & x_{3}
\end{bmatrix}
\begin{bmatrix}
  b \\
  m
\end{bmatrix} - \begin{bmatrix}
  y
\end{bmatrix} \\

 & =
\begin{bmatrix}
b + mx_{1} - y_{1} \\
b + mx_{2} - y_{2} \\
b + mx_{3} - y_{3}
\end{bmatrix}
\end{align}
$$

따라서 위에서 정리했던 $D^{2}$를 다시 정리하면 다음과 같다.

$$
\begin{align}
D^{2} & = (f(x_{1}) - y_{1})^{2} + (f(x_{2}) - y_{2})^{2} + (f(x_{3}) - y_{3})^        {2} \\
      & = (b + mx_{1} - y_{1})^{2} + (b + mx_{2} - y_{2})^{2} + (b + mx_{3} - y_{3})^{2}
\end{align}
$$

위 식에서 $D^{2}$가 최소가 되는 값은 당연히 0이다.  
따라서 풀어야 할 linear system은 다음과 같다.

$$
\begin{align}
(b + mx_{1} - y_{1}) + (b + mx_{2} - y_{2}) + (b + mx_{3} - y_{3}) & = 0 \\
x_{1}(b + mx_{1} - y_{1}) + x_{2}(b + mx_{2} - y_{2}) + x_{3}(b + mx_{3} - y_{3}) & = 0
\end{align}
$$

이를 matrix form으로 나타내면 다음과 같다.

$$
\begin{bmatrix}
1     & 1     & 1     \\
x_{1} & x_{2} & x_{3}
\end{bmatrix}
\begin{bmatrix}
b + mx_{1} - y_{1} \\
b + mx_{2} - y_{2} \\
b + mx_{3} - y_{3}
\end{bmatrix}
$$

이를 조금 더 명확히 정리하자면 다음과 같다.  

$$
\begin{bmatrix}
1     & 1     & 1     \\
x_{1} & x_{2} & x_{3}
\end{bmatrix}
\left(
\begin{bmatrix}
1 & x_{1} \\
1 & x_{2} \\
1 & x_{3}
\end{bmatrix}
\begin{bmatrix}
b \\
m
\end{bmatrix}
-
\begin{bmatrix}
y_{1} \\
y_{2} \\
y_{3}
\end{bmatrix}
\right)
=
\begin{bmatrix}
0 \\
0
\end{bmatrix}
$$

여기서 transformation에 대한 T를 치환하면 다음과 같다.

$$
\begin{align}
M^{T}
\left(
M\begin{bmatrix}
b \\
m
\end{bmatrix}
-
\begin{bmatrix}
y_{1} \\
y_{2} \\
y_{3}
\end{bmatrix}
\right)
& =
\begin{bmatrix}
0 \\
0
\end{bmatrix} \\
M^{T}(M
\begin{bmatrix}
f
\end{bmatrix}
-\begin{bmatrix}
y
\end{bmatrix})
& =
0 \\
M^{T}M
\begin{bmatrix}
f
\end{bmatrix}
- M^{T}
\begin{bmatrix}
y
\end{bmatrix}
& =
0
\end{align}
$$

이를 $f$에 대해 정리하면 다음과 같다.

$$
\begin{align}
M^{T}M
\begin{bmatrix}
f
\end{bmatrix}
& = M^{T}
\begin{bmatrix}
y
\end{bmatrix} \\
[f]
& = (M^{T}M)^{-1}M^{T}
\begin{bmatrix}
y
\end{bmatrix}
\end{align}
$$
