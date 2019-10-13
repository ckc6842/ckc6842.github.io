---
title: "Introduction to 3D Computer Graphics"
categories:
  - Computer Graphics
tags:
  - Computer Graphics
---

# Computer Graphics?
Computer graphics는 컴퓨터를 사용해서 이미지를 그리는 모든 행위를 일컫는다.  
그 중에서도 3D computer graphics는 컴퓨터를 통해 3차원 기반의 기하학적 데이터를 2차원 기반의 이미지로 그려 출력하는 것을 뜻한다.

### Vector image
3D 게임, 애니메이션에서 사용하는 지오메트리 데이터는 데카르트 좌표계 기반의 데이터 형태로 저장되어 있다.  
정점과 선, 면 등으로 이루어진 이러한 형태의 이미지를 vector image이라고 한다.

### Raster image
디스플레이 기기는 pixel 기반의 2D 좌표계 형태로 구성되어 있다.  
화면에 출력하기 위한 pixel 기반의 좌표계를 따르는 이미지를 raster image라고 한다.

즉, 3D computer graphics는 3D 기반의 vector image 데이터를 2D 기반의 raster image로 변환하여 출력하는 일련의 과정이라고 볼 수 있다.


---


# 3D Computer Graphics Pipeline and Terms
## Modeling
Modeling은 오브젝트의 기하학적 형태를 결정하는 과정이다.
Modeling 방식에는 Polygon mesh, NURBS(Non-uniform rational B-spline) 등의 방식이 있다.

### Polygon mesh
정점과 선, 면 등으로 구성된 polygon mesh 기반의 modeling 방식이다.  
Polygon mesh의 구성 요소는 다음과 같다.
* Vertex: 데카르트 좌표계 상의 정점
* Edge: 두 개의 vertices를 이어 만든 선
* Face: 세 개 이상의 맞닿은 edges로 구성된 면
* Polygon: 양면의 faces, 일반적으로 face == polygon
* Mesh: 두 개 이상의 맞닿은 faces로 구성된 오브젝트
* Material: mesh에 적용할 material 목록, 다수의 material을 적용할 수 있음
* UV: texture를 적용하기 위한 좌표계, mesh의 구성 vertices를 2D 기반 좌표계에 mapping

## Layout
각 model을 화면 상 어느 위치에 출력할지 결정하는 과정이다.
Model이 scene의 어느 공간에 위치하는지, 크기는 어느 정도인지, camera는 scene의 어느 지점을 바라보는지 등을 결정한다.

## Material
각 model의 색상을 어떻게 출력할지 결정하는 요소이다.  
구성 요소는 다음과 같다.
* Shader: model의 vertex, 혹은 화면 상의 pixel에 색상을 부여하기 위한 규칙, 일반적으로 빛 반사 등 재질의 속성을 계산함
* Texture: Mesh의 UV에 대응하는 2D raster image로 흔히 map이라고 통칭하기도 함, 하나의 material에 다수의 map을 적용할 수 있음
  - Color map
  - Displace / Bump map
  - Normal map
  - Specular map

## Rendering
Model 데이터에 layout 기반으로 rasterization 후 material 값을 적용하여 화면에 출력하는 과정이다.