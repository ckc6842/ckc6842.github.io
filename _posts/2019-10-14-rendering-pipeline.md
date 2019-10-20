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
임베디드 환경을 위한 OpenGL ES와 Web을 위한 WebGL 등의 파생된 API가 있다.  
OpenGL은 GPU를 사용해서 하드웨어 가속 렌더링을 지원한다.  
GPU는 CPU와는 달리 다수의 코어를 가지고 있기 때문에 병렬 처리 된 다수의 간단한 계산에 유리하다.

| ![gpu acceleration]({{site.url}}/assets/images/gpu_acceleration.png) |
|:--:|
| *GPU acceleration (출처: [NVIDIA: GPU 가속 컴퓨팅이란?](https://kr.nvidia.com/object/what-is-gpu-computing-kr.html){:target="_blank"})* |

## Prerequisite Terms

### Primitives (기초 도형 요소)
OpenGL은 point, line, triagle의 세 종류에서 파생되는 10가지의 primitive를 지원한다.

| ![primitives]({{site.url}}/assets/images/primitives.png) |
|:--:|
| *Primitives (출처: [Wikipedia: Grafisches Primitiv](https://de.wikipedia.org/wiki/Grafisches_Primitiv){:target="_blank"})* |

렌더링 과정에서 다각형의 polygon을 위의 primitive로 쪼개어 처리한다.

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

| ![rendering pipeline]({{site.url}}/assets/images/RenderingPipeline.png) |
|:--:|
| *(출처: [OpenGL Wiki: Rendering Pipeline Overview](https://www.khronos.org/opengl/wiki/Rendering_Pipeline_Overview){:target="_blank"})* |

위 과정 중 유저가 개입할 수 있는 과정은 vertex shader, tesselation, geometry shader, fragment shader이다.  
이 중 vertex shader와 fragment shader는 OpenGL 2.0 이상부터, geometry shader는 3.2부터, tesselation은 4.0부터 지원된다.

## Vertex Specification
이 단계에서는 전체 렌더링 과정에서 처리할 vertex data를 설정한다.  
3D 공간 상에서 vertex는 위치에 대한 3개의 숫자 배열(x, y, z)과 다양한 속성 값들을 가지고 있고, 그리고자 하는 대상은 vertex들의 배열로 표현된다.  

Vertex 배열을 GPU 메모리에 할당하기 위해 **Vertex Buffer Objects(VBO)**를 활용한다.  
그리고 VBO에 저장된 데이터의 레퍼런스를 **Vertex Array Object(VAO)**를 통해 필요할 때 불러 쓸 수 있도록 한다.  
VAO는 VBO의 데이터를 어떠한 속성으로 읽어 사용할 지 결정한다.  
속성 정보로는 vertex의 position, normal, color, UV 등의 정보가 있다.

한편, 여러 개의 맞닿은 polygon을 표현하다보면 불가피하게 vertex의 정보가 중복되는 문제가 발생한다.  
**Element Array Buffer(EBO)**를 통해 index 정보를 전달하면 vertex를 재활용해서 VBO의 크기를 줄일 수 있다.  

| ![indexing]({{site.url}}/assets/images/indexing.png) |
|:--:|
| *Indexing (출처: [opengl-tutorial: Tutorial 9: VBO Indexing](http://www.opengl-tutorial.org/intermediate-tutorials/tutorial-9-vbo-indexing/){:target="_blank"})* |


## Vertex Shader
이 단계에서는 3D 좌표계 상에 있는 vertex data를 화면에 표시하기 위해 pixel 좌표계로 변환하는 작업을 한다.  
통칭 **MVP Matrix** 연산을 통해 각 vertex의 screen 좌표를 구하고, vertex의 normal을 계산하는 과정을 거친다.  
- Model matrix: mesh의 위치를 표현한 좌표계
- View matrix: 카메라가 보는 시점을 나타낸 좌표계
- Projection matrix: 화면에 시점을 투영하기 위한 좌표계

| ![coordinate systems]({{site.url}}/assets/images/coordinate_systems.png) |
|:--:|
| *Coordinate system (출처: [Learn OpenGL: Coordinate Systems](https://learnopengl.com/Getting-started/Coordinate-Systems){:target="_blank"})* |

또한 이 단계에서는 vertex의 위치를 변경하는 작업을 할 수 있다.  
이를 활용하여 mesh의 형태를 동적으로 변경하거나, 애니메이션을 만들 수 있다.

shader 연산은 **GLSL(OpenGL Shader Language)**이라는 언어를 사용한다.  
연산 과정에서 처리하는 변수들은 다음과 같다.  
### Uniform / Varying
- uniform: 애플리케이션에서 shader로 전달하는 읽기 전용 변수, matrix나 vector 값 등을 전달하여 계산에 사용
- varying: vertex shader에서 처리한 값을 fragment로 전달하는 변수

### Output
- gl_Position: 연산이 완료된 vertex의 좌표 값

## Tesselation
이 단계에서는 mesh를 구성하고 있는 polygon을 잘게 나누어 mesh의 표현을 더 정밀하고 부드럽게 한다.

| ![tesselation]({{site.url}}/assets/images/tesselation.png) |
|:--:|
| *Tesselation (출처: [Wikipedia: Tesselation (computer graphics)](https://en.wikipedia.org/wiki/Tessellation_(computer_graphics)){:target="_blank"})* |

## Geometry Shader
이 단계에서는 사용자의 정의에 따라 primitive 단위의 입력을 받아 새로운 primitive를 생성하거나 변형하는 작업을 한다.  

## Vertex Post Processing
이 단계에서는 화면에 결과물을 그리기 위한 fragment 기반의 작업을 수행하기 전, 마지막으로 vertex 연산을 수행한다.
유저가 설정한 화면 상에서 보이지 않는 vertex들을 **clipping** 해서 제거하고 다음 과정으로 넘겨준다.

## Primitive Assembley
이 단계에서는 vertex들을 일련의 primitive로 변환하는 작업을 수행한다.  
변환된 primitive들은 **Face culling**이라는 단계를 거쳐 카메라를 기준으로 한 face의 앞/뒷면을 구분한다.  
Face culling을 통해 구분된 앞/뒷면은 rendering 과정에서 뒷면을 제외하고 그리는 식으로 연산량을 줄이거나, fragment shader에서 활용한다.

| ![winding order]({{site.url}}/assets/images/winding_order.png) |
|:--:|
| *Winding order (출처: [OpenGL Wiki: Face Culling](https://www.khronos.org/opengl/wiki/Face_Culling){:target="_blank"})* |


## Rasterization
이 단계에서는 primitive들을 pixel 좌표계 기반의 fragment에 대응하는 작업을 수행한다.
화면 pixel에 대응하는 색상, depth 등의 값들을 fragment에 저장한다.

| ![rasterization]({{site.url}}/assets/images/rasterization.gif) |
|:--:|
| *Rasterization (출처: [Wikipedia: Rasterization](https://en.wikipedia.org/wiki/Rasterisation){:target="_blank"})* |


## Fragment Shader
이 단계에서는 rasterization의 결과로 fragment에 저장된 값들을 유저가 정의한 코드를 기반으로 수정한다.  
일반적으로는 shading이라고 부르는 색상을 결정하는 과정을 거친다.  
물체의 표면이 빛을 어떻게 반사하는지, 그로 인해 색상은 어떻게 바뀌는지 연산하는 과정이다.  
또한 depth, stencil buffer를 활용해 특별한 처리를 하거나, vertex의 uv를 기준으로 texture를 입히는 작업을 수행하기도 한다.

| ![phong shading]({{site.url}}/assets/images/phong_shading.jpg) |
|:--:|
| *Phong shading (출처: [Wikipedia: Phong shading](https://en.wikipedia.org/wiki/Phong_shading){:target="_blank"})* |

Fragment shader에서 일반적으로 다루는 변수들은 다음과 같다.  
### Input
- gl_FragCoord: fragment의 위치 값
- unifrom: vertex shader와 동일
- varying: vertex shader 연산 결과로 전달 받은 변수

### Output
- gl_FragColor: 연산이 완료된 fragment color
- gl_FragData[n]: bind된 framebuffer가 여러개 일 때 n번째 buffer의 gl_FragColor


## Per-Sample Operation
이 단계에서는 각 fragment들을 실제 이미지로 표현할 지 결정하는 과정을 거친다.  
결정을 위한 과정으로 아래와 같은 다양한 test가 있다.  

### Scissor Test
이 단계에서는 유저가 설정한 특정 범위 안의 fragment만 그리고 나머지 fragment는 폐기(discard)한다.  

### Depth Test
이 단계에서는 depth buffer에 기록된 fragment 별 depth 값을 기준으로 fragment를 그릴 지 말지 결정한다.  
depth 값은 카메라로부터 얼마나 먼지 기록한 값으로, vertex post processing 단계에서 자동으로 작성되고, fragment shader에서 유저의 정의에 따라 수정된다.  
일반적으로 동일 pixel 기준, 화면에서 가까운 fragment만 그리고 나머지는 폐기한다.

| ![depth buffer]({{site.url}}/assets/images/depth_testing.png) |
|:--:|
| *Depth buffer (출처: [Learn OpenGL: Depth testing](https://learnopengl.com/Advanced-OpenGL/Depth-testing){:target="_blank"})* |

### Stencil Test
이 단계에서는 stencil buffer에 기록된 fragment 별 값을 기준으로 fragment를 그릴 지 말지 결정한다.  
stencil buffer는 유저가 정의한 데이터이다.

| ![stencil test]({{site.url}}/assets/images/stencil_buffer.png) |
|:--:|
| *Stencil testing (출처: [Learn OpenGL: Stencil testing](https://learnopengl.com/Advanced-OpenGL/Stencil-testing){:target="_blank"})* |

### Blending
이 단계에서는 fragment shader의 결과물인 fragment 색상들을 혼합한다.  
다양한 blending option을 사용해서 혼합 방식을 다양하게 결정할 수 있다.  
이 blending option은 fragment shader의 결과로 들어온 값(source)과, framebuffer에 이미 그려져 있는 값(destination) 사이의 연산을 결정한다.  
일반적으로 투명한 오브젝트를 나타내거나 후처리(post-processing)를 할 때 많이 쓰인다.  


# References
* NVIDIA: GPU 가속 컴퓨팅이란? ([https://kr.nvidia.com/object/what-is-gpu-computing-kr.html](https://kr.nvidia.com/object/what-is-gpu-computing-kr.html){:target="_blank"})

---

* OpenGL Wiki
  - Rendering Pipeline Overview ([https://www.khronos.org/opengl/wiki/Rendering_Pipeline_Overview](https://www.khronos.org/opengl/wiki/Rendering_Pipeline_Overview){:target="_blank"})
  - Vertex Specification ([https://www.khronos.org/opengl/wiki/Vertex_Specification](https://www.khronos.org/opengl/wiki/Vertex_Specification){:target="_blank"})
  - Face Culling ([https://www.khronos.org/opengl/wiki/Face_Culling](https://www.khronos.org/opengl/wiki/Face_Culling){:target="_blank"})

---

* Wikipedia
  - Tesselation (computer graphics) ([https://en.wikipedia.org/wiki/Tessellation_(computer_graphics)](https://en.wikipedia.org/wiki/Tessellation_(computer_graphics)){:target="_blank"})
  - Rasterization ([https://en.wikipedia.org/wiki/Rasterisation](https://en.wikipedia.org/wiki/Rasterisation){:target="_blank"}))

---

* Learn OpenGL
  - Coordinate Systems ([https://learnopengl.com/Getting-started/Coordinate-Systems](https://learnopengl.com/Getting-started/Coordinate-Systems){:target="_blank"})
  - Depth testing ([https://learnopengl.com/Advanced-OpenGL/Depth-testing](https://learnopengl.com/Advanced-OpenGL/Depth-testing){:target="_blank"})
  - Stencil testing ([https://learnopengl.com/Advanced-OpenGL/Stencil-testing](https://learnopengl.com/Advanced-OpenGL/Stencil-testing){:target="_blank"})
  - Blending ([https://learnopengl.com/Advanced-OpenGL/Blending](https://learnopengl.com/Advanced-OpenGL/Blending){:target="_blank"})