---
title: Get the transformation matrix of coordinate system using SOLIDWORKS API
caption: Get Coordinate System Transformation
description: VBA macro to get the 4x4 transformation matrix from the selected coordinate systems and output the result in the immediate window
image: coordinate-system.png
labels: [transform,coordinate system]
---
![特征管理器树中的坐标系](coordinate-system.png){ width=450 }

这个VBA宏从特征管理器树中选择的坐标系中提取4x4的[转换矩阵](/solidworks-api/geometry/transformation/)。

逗号分隔的结果将输出到VBA编辑器的即时窗口（Ctrl+G）中。

![矩阵输出到VBA编辑器的即时窗口](maxtrix-output-immediate.png){ width=350 }

{% code-snippet { file-name: Macro.vba } %}