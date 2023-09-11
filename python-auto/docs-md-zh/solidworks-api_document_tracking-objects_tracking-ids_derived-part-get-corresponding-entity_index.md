---
caption: 获取派生部件的对应实体
title: 使用SOLIDWORKS API获取派生部件中的对应实体（面、边和顶点）
description: VBA宏演示了如何使用SOLIDWORKS API在派生部件中找到输入部件的对应实体
---
[IPartDoc::InsertPart3](https://help.solidworks.com/2019/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IPartDoc~InsertPart3.html) API允许将派生部件插入到另一个部件中。然而，与[组件](/solidworks-api/document/assembly/context#converting-the-pointers)类似，找到输入部件的对应实体的API是不可用的。

这个VBA宏演示了一个性能高效的解决方法来解决这个限制。

## 运行宏

* 打开源部件（这是要插入到另一个部件中的部件）。此部件必须已保存在磁盘上
* 选择一个或多个实体（面、边、顶点）。如果是多实体部件，则可以在不同的实体中选择
* 运行宏。宏将索引输入并停止执行
* 打开或创建需要插入源部件的新部件
* 继续执行宏
* 结果是插入了派生部件，并选择了所有对应的实体

{% code-snippet { file-name: Macro.vba } %}