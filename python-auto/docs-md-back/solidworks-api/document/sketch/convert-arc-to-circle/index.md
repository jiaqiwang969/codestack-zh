---
title: Convert arc to circle by merging end points using SOLIDWORKS API
caption: Convert Arc To Circle
description: VBA macro to convert sketch arc to a sketch circle by adding the merge relation between start and end points using SOLIDWORKS API
image: sketch-arc.png
labels: [sketch,arc,circle,merge,relation]
---
![草图弧线](sketch-arc.png){ width=350 }

这个VBA宏示例演示了如何在选定的草图弧线的起点和终点之间应用合并草图关系，将其转换为草图圆形。这相当于手动拖动点直到合并或在关系管理器中添加合并草图关系。

{% code-snippet { file-name: Macro.vba } %}