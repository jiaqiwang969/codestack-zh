---
title: Handling the common events of SOLIDWORKS file using SwEx.AddIn framework
caption: Common Events
description: Handling of common events (rebuild, selection, configuration change, item modification, custom property modification etc.) using documents management functionality in SwEx.AddIn Framework
toc-group-name: labs-solidworks-swex
labels: [events,rebuild,selection]
---
SwEx.AddIn框架通过通用的[DocumentHandler](https://docs.codestack.net/swex/add-in/html/T_CodeStack_SwEx_AddIn_Core_DocumentHandler.htm)暴露了常见事件：

* 保存
* 选择
* 访问第三方数据
* 修改自定义属性
* 修改项目
* 配置更改
* 重建
* 尺寸更改

调用[ISwAddInEx.CreateDocumentsHandler](https://docs.codestack.net/swex/add-in/html/M_CodeStack_SwEx_AddIn_Base_ISwAddInEx_CreateDocumentsHandler.htm)创建一个通用的事件处理程序。

建议使用[HandleCreated](https://docs.codestack.net/swex/add-in/html/E_CodeStack_SwEx_AddIn_Base_IDocumentsHandler_1_HandlerCreated.htm)通知来订阅文档事件，该通知将通知新文档加载。

从[Destroyed](https://docs.codestack.net/swex/add-in/html/E_CodeStack_SwEx_AddIn_Core_DocumentHandler_Destroyed.htm)通知中取消订阅事件。

{% code-snippet { file-name: EventsAddIn.* } %}

事件处理程序提供有关事件的其他信息，例如它是预通知还是后通知以及任何其他参数。请查阅API参考以获取有关传递参数的更多信息。

{% code-snippet { file-name: EventsAddIn.EventHandlers.* } %}