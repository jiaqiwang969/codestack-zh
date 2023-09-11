---
title: 使用SOLIDWORKS API遍历组件或模型的所有尺寸
caption: 遍历所有尺寸
description: 使用SOLIDWORKS API，通过VBA宏遍历所选组件或活动文档中所有特征的所有尺寸，并将尺寸名称和值输出到输出窗口
image: dimensions.png
labels: [尺寸,显示尺寸,遍历]
---
![焊接特征草图中的尺寸](dimensions.png)

这个VBA宏演示了如何使用SOLIDWORKS API从活动SOLIDWORKS文档或组件（如果选择了组件）中遍历所有特征的尺寸。

宏将把尺寸名称和当前系统单位的值输出到VBA的即时窗口中。

~~~
D1@Sketch1=0.15
D2@Sketch1=2.0
RI@Sketch11=0.008
~~~

> 该宏将排除所有重复的尺寸，因为在某些情况下（例如焊接特征），同一个尺寸可能同时存在于草图和结构成员特征中。

{% code-snippet { file-name: Macro.vba } %}