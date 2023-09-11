---
title: Create vector normal to screen view using SOLIDWORKS API
caption: Create Vector Normal To Screen View
description: Example demonstrates how to draw a sketch line which is perpendicular (normal) to the current view orientation relative to the screen
image: sw-view-screen-transformation.png
labels: [example, normal, screen, solidworks api, transformation, view]
redirect-from:
  - /2018/04/solidworks-api-transformation-create-vector-normal-to-screen-view.html
---

这个示例演示了如何使用SOLIDWORKS API绘制与屏幕相对于当前视图方向垂直（正交）的草图线。

该线将从屏幕中间的点开始，并且垂直于屏幕方向。这意味着最初它将被渲染为一个点，直到视图旋转。

使用[SOLIDWORKS API的IModelView::Transform](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodelview~transform.html)属性来提取当前视图方向的转换矩阵。

![与当前图形视图垂直的线条](sw-view-screen-transformation.png){ width=320 height=208 }

{% code-snippet { file-name: Macro.vba } %}