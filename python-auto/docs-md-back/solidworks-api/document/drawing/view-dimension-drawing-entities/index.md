---
title: Dimension visible drawing entities from view using SOLIDWORKS API
caption: Dimension Visible Entities
description: Find and dimension the longest visible entity in the drawing view using SOLIDWORKS API
image: longest-edge-dimension.png
labels: [drawing,dimension,visible entities]
---
![在绘图视图中标注最长的边的尺寸](longest-edge-dimension.png){ width=250 }

本示例演示了如何使用SOLIDWORKS API在所选绘图视图中为最长的边添加线性尺寸。

此宏遍历绘图视图中的所有可见实体，计算边的长度并找到最长的边。只有最长的边可以被标注尺寸（即它是线性或圆形边）时，宏才能正常工作。

从[IView::GetVisibleEntities](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iview~getvisibleentities.html)返回的实体已经处于绘图视图上下文中，可以直接通过[SOLIDWORKS API的IEntity::Select4](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ientity~select4.html)方法选择它们，无需调用[IView::SelectEntity](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iview~selectentity.html)函数。

尺寸的位置是通过将尺寸边的中点在法线曲线方向（切线方向和图纸Z轴的叉乘）上偏移边长的20%来计算的。与[图纸上下文中的绘制](/solidworks-api/document/drawing/sheet-context-sketch/)不同，在定位尺寸时，不需要将图纸比例乘以视图变换矩阵。

{% code-snippet { file-name: Macro.vba } %}