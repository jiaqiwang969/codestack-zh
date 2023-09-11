---
title: Insert BOM balloons into drawing view using SOLIDWORKS API
caption: Insert BOM Balloons
description: VBA macro to automatically insert BOM balloons into an existing drawing view of the current sheet using SOLIDWORKS API
image: bom-balloons.png
labels: [BOM, balloon]
---
![零件中的BOM气球](bom-balloons.png)

这个VBA宏演示了如何使用SOLIDWORKS API，在活动绘图工作表的第一个绘图视图中为所有可见零件插入气球。

宏将遍历所有可见零件和视图的所有可见实体，并将气球链接到项目编号，附加到第一个可见实体。

气球引线将附加到相应边缘的中间位置。而气球本身将从边缘的中间位置偏移10毫米的X和Y方向。

{% code-snippet { file-name: Macro.vba } %}