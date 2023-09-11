---
title: Get sketch lines of sheet metal sketched bend using SOLIDWORKS API
caption: Get Sketch Lines For Sheet Metal Sketched Bend Feature
description: Finds all straight lines (bends) of the sheet metal Sketched Bend feature and selects all segments
image: sheet-metal-sketched-bend.png
labels: [example, sheet metal, sketched bend, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-sheet-metal-get-sketched-bends.html
---
使用SOLIDWORKS API，宏程序可以找到钣金*弯曲特征*中的所有直线（弯曲），并选择所有线段。

![钣金弯曲特征的草图](sheet-metal-sketched-bend.png){ width=400 }

目前没有直接的SOLIDWORKS API方法可以获取弯曲，但是弯曲在由钣金特征拥有的草图中表示为草图线段。因此，为了找到弯曲，需要找到该草图并解析其内容。

{% code-snippet { file-name: Macro.vba } %}