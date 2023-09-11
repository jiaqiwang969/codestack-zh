---
title: 仅用于API选择SOLIDWORKS对象
caption: 仅用于API选择对象
description: 该示例演示了如何仅通过选择对象进行API操作（无图形选择），同时保留当前用户的选择。
image: extrude-direction-up-to-surface.png
labels: [选择, 拉伸]
---
![沿着线方向延伸的挤压草图弧到平面表面](extrude-direction-up-to-surface.png){ width=500 }

该示例演示了如何通过仅选择对象进行API操作（无图形选择），同时保留当前用户的选择，从而在SOLIDWORKS零件中创建挤压特征。

运行宏的步骤如下：

* 下载示例文件并在SOLIDWORKS中打开[挤压选择示例](extrude-selection-example.SLDPRT)
* 选择任意对象（例如前平面和右平面）
* 逐步调试宏。宏会在数据库中直接预先选择所需的对象，用于挤压特征（即用户看不到）

结果是创建了指定方向的挤压，延伸到指定的表面，并且保留了所有原始用户的选择。

{% code-snippet { file-name: Macro.vba } %}