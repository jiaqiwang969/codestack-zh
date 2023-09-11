---
title: 使用SOLIDWORKS API将弧线转换为圆形通过合并端点
caption: 将弧线转换为圆形
description: 使用SOLIDWORKS API在选定的草图弧线的起点和终点之间添加合并关系，将其转换为草图圆形的VBA宏示例
image: sketch-arc.png
labels: [草图,弧线,圆形,合并,关系]
---
![草图弧线](sketch-arc.png){ width=350 }

这个VBA宏示例演示了如何在选定的草图弧线的起点和终点之间应用合并草图关系，将其转换为草图圆形。这相当于手动拖动点直到合并或在关系管理器中添加合并草图关系。

{% code-snippet { file-name: Macro.vba } %}