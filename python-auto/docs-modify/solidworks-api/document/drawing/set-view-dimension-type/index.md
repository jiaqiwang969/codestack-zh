---
caption: Set View Dimension Type
title: Macro to set dimension type for all views in the active SOLIDWORKS drawing
description: VBA macro which sets dimension type (projected or true) for all drawing view in the active SOLIDWORKS drawing document
image: view-dimension-type.png
---
![视图尺寸类型](view-dimension-type.png)

这个VBA宏会为活动SOLIDWORKS绘图中所有工作表的所有绘图视图设置尺寸类型（投影或真实）。

将**DIMS_TRUE**常量设置为**True**以将所有尺寸类型设置为**真实**。将**DIMS_TRUE**常量设置为**False**以将所有尺寸类型设置为**投影**。

{% code-snippet { file-name: Macro.vba } %}