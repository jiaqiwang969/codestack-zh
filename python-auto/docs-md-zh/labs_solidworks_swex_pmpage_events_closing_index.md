---
title: SOLIDWORKS 属性管理器页面关闭事件处理
caption: 关闭
description: SwEx.PMPage 框架中处理 SOLIDWORKS 属性管理器页面关闭事件的概述
toc-group-name: labs-solidworks-swex
order: 1
---
## 关闭前事件
[PropertyManagerPageHandlerEx::Closing](https://docs.codestack.net/swex/pmpage/html/E_CodeStack_SwEx_PMPage_PropertyManagerPageHandlerEx_Closing.htm) 事件在属性管理器页面即将关闭时触发。

框架传递了关闭的原因和 [closing argument](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Base_ClosingArg.htm)，允许取消属性管理器页面的关闭并向用户显示错误提示。

{% code-snippet { file-name: Events.Closing.* } %}

此事件在属性管理器页面对话框仍可见时触发。在此处理程序中不应执行重建操作，包括直接重建以及任何新的特征或几何体的创建或修改（除了临时体）。请注意，某些操作（如保存）可能也不受支持。一般来说，如果在属性页面打开时无法从用户界面执行某个操作，则也不应通过 API 从关闭事件调用该操作。否则，这可能会导致不稳定性，包括崩溃。请使用[关闭后事件](#post-closing-event)来执行任何重建操作。

在某些情况下，需要在属性管理器页面保持打开的同时执行此操作。通常情况下，当页面支持固定（[PageOptionsAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_PageOptionsAttribute.htm) 中的 [swPropertyManagerOptions_PushpinButton](https://help.solidworks.com/2016/english/api/swconst/SOLIDWORKS.Interop.swconst~SOLIDWORKS.Interop.swconst.swPropertyManagerPageOptions_e.html) 标志）时会发生这种情况。在这种情况下，需要在 [PageOptionsAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_PageOptionsAttribute.htm) 中设置 [swPropertyManagerOptions_LockedPage](https://help.solidworks.com/2016/english/api/swconst/SOLIDWORKS.Interop.swconst~SOLIDWORKS.Interop.swconst.swPropertyManagerPageOptions_e.html) 标志。这将启用从 [PropertyManagerPageHandlerEx::Closing](https://docs.codestack.net/swex/pmpage/html/E_CodeStack_SwEx_PMPage_PropertyManagerPageHandlerEx_Closing.htm) 事件中进行重建操作和特征创建的支持。

## 关闭后事件

[PropertyManagerPageHandlerEx::Closed](https://docs.codestack.net/swex/pmpage/html/E_CodeStack_SwEx_PMPage_PropertyManagerPageHandlerEx_Closed.htm) 事件在属性管理器页面关闭时触发。

使用此处理程序执行所需的操作。

{% code-snippet { file-name: Events.Closed.* } %}