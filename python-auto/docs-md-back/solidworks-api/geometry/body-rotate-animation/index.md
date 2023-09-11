---
title: Create body rotation animation using SOLIDWORKS API
caption: Create Body Rotation Animation
description: VBA example to create a rotation animation of a selected body around Y axis using SOLIDWORKS API and temp bodies
image: body-rotate.gif
labels: [animation,rotate,temp body]
---
![物体旋转动画](body-rotate.gif)

这个VBA示例演示了如何使用SOLIDWORKS API在零件文档中创建一个选定物体的旋转动画。

在特征管理器树中不会创建额外的特征。这个宏**不使用**SOLIDWORKS运动研究。物体围绕原点的Y轴旋转。动画使用临时物体创建，原始物体或特征管理器树不受影响。

从特征管理器树中选择物体，然后运行宏。

![在特征管理器树中选择的物体](feature-tree-body-selected.png){ width=250 }

预览的物体会被创建并旋转，直到选择被清除。当宏停止时，原始物体会恢复到原始状态。

{% code-snippet { file-name: Macro.vba } %}