---
title: Add move-copy body feature with coincident mate using SOLIDWORKS API
caption: Add Move-Copy Body Feature With Mate
description: C# VSTA macro example to create move-copy body feature and add coincident mate between the largest face of the body and front plane using SOLIDWORKS API
image: move-copy-body-mate-pmp.png
labels: [move-copy body,mates]
---
![添加了共面约束的移动-复制体属性管理器页面](move-copy-body-mate-pmp.png){ width=150 }

这是一个C# VSTA宏示例，它可以找到所选体的最大平面面，并在零件中插入移动-复制体特征，并使用SOLIDWORKS API在最大面和前平面之间添加共面约束。

* 打开零件文档
* 选择包含平面面的任何体
* 运行宏。结果是通过[SOLIDWORKS API的IFeatureManager::InsertMoveCopyBody2](https://help.solidworks.com/2016/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ifeaturemanager~insertmovecopybody2.html)方法插入了移动-复制体特征。然后使用[SOLIDWORKS API的IMoveCopyBodyFeatureData::AddMate](https://help.solidworks.com/2016/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IMoveCopyBodyFeatureData~AddMate.html)方法在体的最大面和前平面之间添加了共面约束。

{% code-snippet { file-name: SolidWorksMacro.cs } %}