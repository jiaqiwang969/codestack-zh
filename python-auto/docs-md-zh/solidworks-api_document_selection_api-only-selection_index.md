---
title: 仅用于API选择SOLIDWORKS对象
caption: 仅用于API选择对象
description: 示例展示了如何仅用于API目的选择对象（不包括图形选择），同时保留当前用户的选择
image: extrude-direction-up-to-surface.png
labels: [选择, 拉伸]
---
![沿着线方向将挤压的草图弧形延伸到平面表面](extrude-direction-up-to-surface.png){ width=500 }

这个示例展示了如何通过仅选择用于API目的的输入（不包括图形选择），保留当前用户的选择，在SOLIDWORKS零件中创建挤压特征。

运行宏的步骤：

* 下载示例文件并在SOLIDWORKS中打开[挤压选择示例](extrude-selection-example.SLDPRT)
* 选择任意对象（例如前平面和右平面）
* 逐步调试宏。宏会在数据库中直接预先选择所需的对象用于挤压特征（对用户不可见）

结果是创建了指定方向的挤压特征，延伸到指定的表面，并且保留了所有原始用户的选择。

{% code-snippet { file-name: Macro.vba } %}