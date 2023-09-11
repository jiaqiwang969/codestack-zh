---
title: Draw border of the active sheet on the specified layer
caption: Draw Border On Layer
description: VBA macro example demonstrates how to draw a border on the active drawing sheet on the specified layer considering the sheet scale
image: sheet-border.png
labels: [border,layer,scale]
---
![在图层上绘制的工作表边框](sheet-border.png){ width=350 }

这个VBA宏在指定图层上绘制了活动工作表的边框。

宏会考虑工作表的比例尺来计算边框的正确坐标。

{% code-snippet { file-name: Macro.vba } %}