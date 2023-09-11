---
title: 使用SOLIDWORKS API和IModeler接口创建临时实体盒子
caption: 创建盒子实体
description: 使用SOLIDWORKS API和IModeler接口，通过中心点、方向和尺寸创建临时实体的VBA示例
image: box-body.png
labels: [基本体, 盒子, 临时实体, 模型]
---
![盒子实体](box-body.png){ width=250 }

这个VBA示例演示了如何使用SOLIDWORKS API通过提供基面中心点的坐标、方向、宽度、长度和高度来创建和显示临时实体。

宏停止执行并显示实体。继续执行宏以销毁临时实体。

{% code-snippet { file-name: Macro.vba } %}