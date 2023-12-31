---
title: SOLIDWORKS API to create surface loft feature via contours
caption: Create Surface Loft Feature Via Contours
description: Example demonstrates how to create surface loft feature from the contours as the profiles using SOLIDWORKS API
image: lofted-surface-sketch-contours.png
labels: [surface, loft, contour]
---

![使用轮廓作为剖面创建的曲面放样特征](lofted-surface-sketch-contours.png){ width=500 }

该示例演示了如何使用SOLIDWORKS API从轮廓作为剖面创建曲面放样特征。

曲面放样特征不接受草图线段作为剖面实体。这意味着如果只需要使用草图中的几个线段作为剖面（而不是整个草图），则无法通过选择草图线段来创建特征。必须使用草图轮廓来完成。

草图线段在用户界面中也不受支持。当选择线段时，会显示以下选择管理器，允许选择开放或闭合环。

![选择剖面时的选择管理器](selection-manager.png){ width=250 }

* 打开零件并选择草图线段作为剖面。支持任何类型的草图线段（样条线、直线、弧等）。草图中可能有多个线段，只能选择其中几个作为剖面。线段也可以位于不同的草图中。
* 宏将为每个草图线段找到相应的草图轮廓。
* 宏将使用相应的草图轮廓创建曲面放样特征。

> 此宏不是查找相同草图中线段的草图轮廓的最佳性能代码，因为它将遍历草图中的所有线段以查找各个草图线段的相应轮廓。可以修改宏以在一个遍历循环中查找多个草图轮廓，避免重复。

{% code-snippet { file-name: Macro.vba } %}