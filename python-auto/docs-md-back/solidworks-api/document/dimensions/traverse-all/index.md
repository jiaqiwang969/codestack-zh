---
title: Traverse all dimensions of component or model using SOLIDWORKS API
caption: Traverse All Dimensions
description: VBA macro which traverses all dimensions of all features in the selected component or active document using SOLIDWORKS API and outputs the dimension name and value to the output Window
image: dimensions.png
labels: [dimension,display dimension,traverse]
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