---
title: "OpenGL Rendering Pipeline"
categories:
  - Computer Graphics
tags:
  - Computer Graphics
  - OpenGL
---

# OpenGL?
OpenGL(Open Graphics Library)은 computer graphics를 위한 API 라이브러리이다.  
GPU를 사용해서 하드웨어 가속 렌더링을 지원한다.
<!-- 이미지 -->

## Prerequisite Terms

### Primitives (기초 도형 요소)
OpenGL은 point, line, triagle의 세 종류에서 파생되는 10가지의 primitive를 지원한다.  
<!-- 이미지 -->
렌더링 과정에서 다각형의 polygon을 위의 primitive로 쪼개여 처리한다.

### Buffer
프로그래밍에서 buffer는 memory의 블록을 의미한다.  
일반적으로는 데이터를 담아 이동시키는 역할을 하는데, OpenGL에서는 CPU에서 GPU로, 혹은 반대로 데이터를 옮기는 역할을 한다.

### Fragment
화면 상의 pixel에 대응하는 개념이다.
하나의 pixel에 다수의 fragment가 존재 할 수 있다.

<br/>    
---
<br/>
# OpenGL Rendering Pipeline
OpenGL에서의 렌더링은 아래와 같은 과정을 따른다.
<!-- 이미지 -->


## Vertex Specification
이 단계에서는 전체 렌더링 과정에서 처리할 vertex data를 설정한다.  
3D 공간 상에서 vertex는 위치에 대한 3개의 숫자 배열(x, y, z)과 다양한 속성 값들을 가지고 있고, 그리고자 하는 대상은 vertex들의 배열로 표현된다.  

Vertex 배열을 GPU 메모리에 할당하기 위해 Vertex Buffer Objects(VBO)를 활용한다.  
그리고 VBO에 저장된 데이터의 레퍼런스를 Vertex Array Object(VAO)를 통해 필요할 때 불러 쓸 수 있도록 한다.  
VAO는 VBO의 데이터를 어떠한 속성으로 읽어 사용할 지 결정한다.  
속성 정보로는 vertex의 position, normal, color, UV 등의 정보가 있다.

한편, 여러 개의 맞닿은 polygon을 표현하다보면 불가피하게 vertex의 정보가 중복되는 문제가 발생한다.  
<!-- 이미지 -->
Element Array Buffer(EBO)를 통해 index 정보를 전달하면 vertex를 재활용해서 VBO의 크기를 줄일 수 있다.  


## Vertex Shader
이 단계에서는 3D 좌표계 상에 있는 vertex data를 화면에 표시하기 위해 pixel 좌표계로 변환하는 작업을 한다.  
통칭 MVP Matrix 연산을 통해 각 vertex의 world 좌표를 구하고, vertex의 normal을 계산하는 과정을 거친다.  
- Model matrix: mesh의 위치를 표현한 좌표계
- View matrix: 카메라가 보는 시점을 나타낸 좌표계
- Projection matrix: 화면에 시점을 투영하기 위한 좌표계
<!-- 이미지 -->

또한 이 단계에서는 vertex의 위치를 변경하는 작업을 할 수 있다.  
이를 활용하여 mesh의 형태를 동적으로 변경하거나, 애니메이션을 만들 수 있다.

shader 연산은 GLSL(OpenGL Shader Language)이라는 언어를 사용한다.  
<!-- 이미지 -->

### Uniform / Varying
- uniform: 애플리케이션에서 shader로 전달하는 읽기 전용 변수, matrix나 vector 값 등을 전달하여 계산에 사용
- varying: vertex shader에서 처리한 값을 fragment로 전달하는 변수

### Output
- gl_Position: 연산이 완료된 vertex의 좌표 값

## Tesselation
이 단계에서는 mesh를 구성하고 있는 polygon을 잘게 나누어 mesh의 표현을 더 정밀하고 부드럽게 한다.

## Geometry Shader


## Vertex Post Processing
이 단계에서는 화면에 결과물을 그리기 위한 fragment 기반의 작업을 수행하기 전, 마지막으로 vertex 연산을 수행한다.

### Clipping


## Primitive Assembley
이 단계에서는 vertex들을 일련의 primitive로 변환하는 작업을 수행한다.

### Face culling


## Rasterization
이 단계에서는 primitive들을 pixel 좌표계 기반의 fragment에 대응하는 작업을 수행한다.


## Fragment Shader

### Input
- gl_FragCoord: fragment의 위치 값
- varying: 

### Output
- gl_FragColor: 연산이 완료된 fragment color
- gl_FragData[n]: bind된 framebuffer가 여러개 일 때 n번째 buffer의 gl_FragColor

## Per-Sample Operation

### Scissor Test

### Depth Test

### Stencil Test

### Blending

### Draw