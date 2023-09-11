---
title: Create sketch segments in drawing view sketch using SOLIDWORKS API
caption: Create Sketch Segments In Drawing View
description: Creating sketch points and sketch segments directly in the drawing view sketch area using SOLIDWORKS API
image: point-in-drawing-view-sketch.png
labels: [drawing,transform,sketch]
---

![在绘图视图中心创建的点](point-in-drawing-view-sketch.png){ width=350 }

绘图文档中的所有绘图视图都有自己的草图，可以通过[SOLIDWORKS API方法IView::GetSketch](https://help.solidworks.com/2019/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iview~getsketch.html)来获取。

这是一个草图，可以使用[ISketchManager](https://help.solidworks.com/2019/english/api/draftsightapi/Interop.dsAutomation~Interop.dsAutomation.ISketchManager.html)接口绘制草图实体和点。

与[在图纸空间中创建草图段](/solidworks-api/document/drawing/sheet-context-sketch/)不同，添加到视图草图中的段将随视图一起移动，并且在视图进行3D旋转时会进行缩放和旋转。

与装配或零件中的草图类似，需要将模型空间的坐标转换为图纸空间，以便正确定位段。

以下示例演示了如何使用SOLIDWORKS API通过转换找到绘图视图的中点（在图纸坐标系中），并直接在视图中绘制此点。

{% code-snippet { file-name: Macro.vba } %}