---
caption: Get Corresponding Entity Of Derived Part
title: Get corresponding entities (faces, edges and vertices) in the derived part using SOLIDWORKS API
description: VBA macro demonstrates how to find the corresponding entities from the input part in the derived part using SOLIDWORKS API
---
[IPartDoc::InsertPart3](https://help.solidworks.com/2019/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IPartDoc~InsertPart3.html) API允许将派生部件插入到另一个部件中。然而，类似于[组件](/solidworks-api/document/assembly/context#converting-the-pointers)的对应实体的API是不可用的。

这个VBA宏演示了一个性能高效的解决方法来解决这个限制。

## 运行宏

* 打开源部件（这是要插入到另一个部件中的部件）。这个部件必须已经保存在磁盘上
* 选择一个或多个实体（面、边、顶点）。如果是多实体部件，可以在不同的实体中选择
* 运行宏。宏将索引输入并停止执行
* 打开或创建需要插入源部件的新部件
* 继续执行宏
* 结果是插入了派生部件，并且所有对应的实体都被选择了

{% code-snippet { file-name: Macro.vba } %}