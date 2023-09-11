---
title: 使用SOLIDWORKS模型API创建临时环面体
caption: 创建临时环面体
description: 本示例演示了如何使用SOLIDWORKS API从环面创建临时体
image: toroidal-surface.png
labels: [拓扑结构, 几何, 面片, 模型, 圆柱体]
---
![环面体](toroidal-surface.png)

本示例演示了如何使用SOLIDWORKS API从环面创建一个面片体。

几何图形是使用[SOLIDWORKS API的IModeler::CreateToroidalSurface](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeler~createtoroidalsurface.html)方法创建的。

运行宏代码，将显示临时体。可以旋转和选择该体，但它不会显示在特征树中。继续执行宏以销毁该体。

{% code-snippet { file-name: Macro.vba } %}