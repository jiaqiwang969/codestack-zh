---
title: 使用SOLIDWORKS API添加移动-复制体特征和共面约束
caption: 添加移动-复制体特征和共面约束
description: C# VSTA宏示例，使用SOLIDWORKS API在零件中创建移动-复制体特征，并在体的最大面和前平面之间添加共面约束
image: move-copy-body-mate-pmp.png
labels: [移动-复制体, 共面约束]
---
![添加了共面约束的移动-复制体属性管理器页面](move-copy-body-mate-pmp.png){ width=150 }

这是一个C# VSTA宏示例，它可以找到所选体的最大平面面，并在零件中插入移动-复制体特征，并使用SOLIDWORKS API在最大面和前平面之间添加共面约束。

* 打开零件文档
* 选择包含平面面的任何体
* 运行宏。结果是通过[SOLIDWORKS API的IFeatureManager::InsertMoveCopyBody2](https://help.solidworks.com/2016/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ifeaturemanager~insertmovecopybody2.html)方法插入了移动-复制体特征。然后使用[SOLIDWORKS API的IMoveCopyBodyFeatureData::AddMate](https://help.solidworks.com/2016/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IMoveCopyBodyFeatureData~AddMate.html)方法在体的最大面和前平面之间添加了共面约束。

{% code-snippet { file-name: SolidWorksMacro.cs } %}