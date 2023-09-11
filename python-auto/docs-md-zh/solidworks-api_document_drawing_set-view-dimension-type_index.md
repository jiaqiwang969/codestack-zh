---
caption: 设置视图尺寸类型
title: 用于设置活动SOLIDWORKS绘图中所有视图的尺寸类型的宏
description: 这是一个VBA宏，用于设置活动SOLIDWORKS绘图文档中所有绘图视图的尺寸类型（投影或真实）
image: view-dimension-type.png
---
![视图尺寸类型](view-dimension-type.png)

这个VBA宏会为活动SOLIDWORKS绘图中所有工作表的所有绘图视图设置尺寸类型（投影或真实）。

将**DIMS_TRUE**常量设置为**True**以将所有尺寸类型设置为**真实**。将**DIMS_TRUE**常量设置为**False**以将所有尺寸类型设置为**投影**。

{% code-snippet { file-name: Macro.vba } %}