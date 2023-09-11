---
title: Rendering custom 3D graphics with Open GL in SOLIDWORKS API
caption: OpenGL
description: Section contains examples and code snippets for rendering 3D graphics in the model view using SOLIDWORKS API with OpenGL methods
order: 3
labels: [graphics, opengl, render]
redirect-from:
  - /solidworks-api/adornment/open-gl/
---
SOLIDWORKS模型利用3D渲染引擎（如DirectX和OpenGL）在图形区域绘制几何图形。

SOLIDWORKS API允许第三方插件和宏使用[OpenGL](https://en.wikipedia.org/wiki/OpenGL)函数直接将3D图形对象注入到模型层中。

在这种情况下，几何图形被嵌入到图形视图中，并与模型本身一起进行变换。这意味着不需要计算变换矩阵。

OpenGL是最流行的跨平台高性能渲染库，广泛应用于游戏、虚拟现实、CAD等领域。请查阅[文档](https://www.opengl.org/documentation/)以获取有关该库的更多信息。

OpenGL图形应该在[IModelView](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelView.html)接口的[BufferSwapNotify](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dmodelviewevents_bufferswapnotifyeventhandler.html)事件中进行渲染。

当需要显示复杂的图形或动画时，这种渲染技术非常有用，但由于其他限制，创建临时或永久几何图形可能会消耗性能或不可行。

浏览本节的代码示例和宏，演示了使用SOLIDWORKS API中的OpenGL来在视图中渲染对象的用法。