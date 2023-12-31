---
title: Suspend SOLIDWORKS rebuild operation using Geometry++
caption: Suspend Rebuild
description: Suspend SOLIDWORKS rebuild operations in part, assembly and drawing to rebuild in batch to improve performance using Geometry++ add-in
image: icon.png
toc-group-name: labs-solidworks-geometry-plus-plus
---
{% youtube { id: QW3tYaNAfo0 } %}

该命令允许在保留修改尺寸、草图和特征定义的同时，暂时暂停重建操作。

这种方法通过批量模式执行重建操作，大大减少了建模时间。

该命令可在菜单、工具栏和命令管理器选项卡中使用，并作为切换按钮。

当按钮未切换时，暂停重建模式被禁用，重建操作将正常执行。

![工具栏和命令管理器中的暂停重建命令](not-suspended-buttons-state.png)

当按钮切换时，所有重建操作都将被暂停。

![启用暂停重建](suspended-buttons-state.png)

状态栏显示当前暂停的重建操作数量的信息。

![状态栏中的暂停重建数量](status-bar-message.png)

在暂停重建模式下，更改不会被解决，模型将保持不变。在编辑特征定义并关闭属性管理器页面后，编辑的特征下方的所有特征将变为禁用状态（不可编辑），直到重新构建模型。

完成批量编辑后，禁用“暂停重建”按钮，然后点击“重建（ctrl+B）”或“重新生成（ctrl+Q）”命令以更新模型。

> 免责声明：尽管暂停重建的功能是使用SOLIDWORKS API实现的，但禁用重建可能会导致模型出现意外行为。然而，没有报告任何损坏或损坏的问题。请自行承担风险。