---
title: 使用SOLIDWORKS API获取钣金弯曲的草图线
caption: 获取钣金弯曲特征的草图线
description: 使用SOLIDWORKS API找到钣金弯曲特征的所有直线（弯曲）并选择所有线段
image: sheet-metal-sketched-bend.png
labels: [示例, 钣金, 弯曲特征, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-sheet-metal-get-sketched-bends.html
---
使用SOLIDWORKS API，宏程序可以找到钣金*弯曲特征*中的所有直线（弯曲），并选择所有线段。

![钣金弯曲特征的草图](sheet-metal-sketched-bend.png){ width=400 }

目前没有直接的SOLIDWORKS API方法可以获取弯曲，但是弯曲在由钣金特征拥有的草图中表示为草图线段。因此，为了找到弯曲，需要找到该草图并解析其内容。

{% code-snippet { file-name: Macro.vba } %}