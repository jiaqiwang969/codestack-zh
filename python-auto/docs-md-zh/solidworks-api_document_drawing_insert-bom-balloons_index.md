---
title: 使用SOLIDWORKS API在绘图视图中插入BOM气球
caption: 插入BOM气球
description: 使用SOLIDWORKS API，通过VBA宏自动将BOM气球插入当前工作表的现有绘图视图
image: bom-balloons.png
labels: [BOM, 气球]
---
![零件中的BOM气球](bom-balloons.png)

这个VBA宏演示了如何使用SOLIDWORKS API，在活动绘图工作表的第一个绘图视图中为所有可见零件插入气球。

宏将遍历所有可见零件和视图的所有可见实体，并将气球链接到项目编号，附加到第一个可见实体。

气球引线将附加到相应边缘的中间位置。而气球本身将从边缘的中间位置偏移10毫米的X和Y方向。

{% code-snippet { file-name: Macro.vba } %}