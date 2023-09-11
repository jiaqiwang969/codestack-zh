---
title: Untrim face or surface with temporary geometry using SOLIDWORKS API
caption: Create Untrimmed Surface
description: VBA example to create an untrimmed (restored) surface from the selected face with temporary geometry using SOLIDWORKS API
image: untrimmed-surface.png
labels: [trim,curve,untrim]
---
此VBA示例通过执行未修剪操作来恢复所选面的曲面。

此命令类似于特征管理器中的“未修剪曲面”功能，但它使用临时实体而不是特征来执行操作。

在操作中使用的复制曲面是无限的，需要修剪才能形成面。所需边界通过评估输入面的UV的最大和最小值来计算。

![面的UV边界](face-uv.svg){ width=450 }

使用等值曲线提取面指定边界UV处的曲线。计算得到的曲线是无限的，需要在角落处修剪成闭合环路，然后才能修剪和转换为实体。

选择任何面并运行宏。结果曲面将显示在图形区域中，并停止执行宏。继续后，预览将被隐藏。

![输入曲面和未修剪结果](untrimmed-surface.png){ width=450 }

{% code-snippet { file-name: Macro.vba } %}