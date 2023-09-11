---
title: Create temp cylindrical sheet body using SOLIDWORKS modeler API
caption: Create Temp Cylindrical Sheet Body
description: Example demonstrates how to create temp body of a cylindrical sheet
image: cylindrical-surface.png
labels: [topology, geometry, sheet, modeler, cylinder]
---
![圆柱面体](cylindrical-surface.png)

本示例演示了如何使用SOLIDWORKS API从圆柱面创建一个面体。

运行宏代码，将显示临时体。可以旋转和选择该体，但它不会显示在特征树中。继续执行宏代码以销毁该体。

{% code-snippet { file-name: Macro.vba } %}