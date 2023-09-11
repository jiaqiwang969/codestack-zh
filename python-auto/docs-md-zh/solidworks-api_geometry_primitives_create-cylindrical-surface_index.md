---
title: 使用SOLIDWORKS模型API创建临时圆柱面体
caption: 创建临时圆柱面体
description: 本示例演示了如何使用SOLIDWORKS API从圆柱面创建临时体
image: cylindrical-surface.png
labels: [拓扑结构, 几何, 面体, 模型, 圆柱体]
---
![圆柱面体](cylindrical-surface.png)

本示例演示了如何使用SOLIDWORKS API从圆柱面创建一个面体。

运行宏代码，将显示临时体。可以旋转和选择该体，但它不会显示在特征树中。继续执行宏代码以销毁该体。

{% code-snippet { file-name: Macro.vba } %}