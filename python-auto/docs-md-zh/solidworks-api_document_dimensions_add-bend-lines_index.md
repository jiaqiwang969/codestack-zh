---
title: 使用SOLIDWORKS API为弯曲线添加尺寸
caption: 添加弯曲线尺寸
description: 本示例演示了如何使用SOLIDWORKS API在钣金展开图的绘图视图中为弯曲线添加尺寸。
image: sw-bend-lines.png
labels: [弯曲线, 尺寸, 示例, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-dimensions-dimension-bend-lines.html
---
本示例演示了如何使用SOLIDWORKS API在钣金展开图的绘图视图中为弯曲线添加尺寸。

![在钣金展开图绘图中的弯曲线之间添加尺寸](sw-bend-lines.png){ width=400 height=150 }

需要使用带有分配视图的选择数据对象来选择草图线，否则创建尺寸将失败。

使用[IModelDoc2::AddDimension2](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeldoc~adddimension2.html) SOLIDWORKS API来添加尺寸。尺寸定位在坐标(0, 0, 0)处。请参考[尺寸可见实体](/solidworks-api/document/drawing/view-dimension-drawing-entities/)示例中的代码片段来计算最佳尺寸位置。

{% code-snippet { file-name: Macro.vba } %}