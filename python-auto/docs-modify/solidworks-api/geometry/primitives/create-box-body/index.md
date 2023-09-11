---
title: Create temp solid body box using SOLIDWORKS API and IModeler interface
caption: Create Box Body
description: VBA example to create a temp body by center point, direction and size using SOLIDWORKS API and IModeler interface
image: box-body.png
labels: [primitive,box,temp body,modeler]
---
![盒子实体](box-body.png){ width=250 }

这个VBA示例演示了如何使用SOLIDWORKS API通过提供基面中心点的坐标、方向、宽度、长度和高度来创建和显示临时实体。

宏停止执行并显示实体。继续执行宏以销毁临时实体。

{% code-snippet { file-name: Macro.vba } %}