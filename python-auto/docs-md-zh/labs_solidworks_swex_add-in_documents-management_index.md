---
title: 通过SwEx.AddIn框架管理SOLIDWORKS文档生命周期
caption: 文档管理
description: 使用SwEx.AddIn框架管理SOLIDWORKS文档的生命周期（打开、关闭、激活）及其事件
toc-group-name: labs-solidworks-swex
order: 3
---
SwEx.AddIn框架提供了一个实用类来通过创建一个指定的实例处理程序作为模型的包装来管理文档的生命周期。

调用[ISwAddInEx.CreateDocumentsHandler](https://docs.codestack.net/swex/add-in/html/M_CodeStack_SwEx_AddIn_Base_ISwAddInEx_CreateDocumentsHandler__1.htm)方法，并将文档处理程序的类型作为泛型参数传递，或者使用第二个重载来创建一个通用的文档处理程序，该处理程序公开了[常见事件](events/)（例如保存、选择、重建、[第三方存储访问](/labs/solidworks/swex/add-in/third-party-data-storage/)）。

{% code-snippet { file-name: DocMgrAddIn.DocHandlerInit.* } %}

通过实现[IDocumentHandler](https://docs.codestack.net/swex/add-in/html/T_CodeStack_SwEx_AddIn_Base_IDocumentHandler.htm)接口或[DocumentHandler](https://docs.codestack.net/swex/add-in/html/T_CodeStack_SwEx_AddIn_Core_DocumentHandler.htm)类来定义文档处理程序。

{% code-snippet { file-name: DocMgrAddIn.DocHandlerDefinition.* } %}

重写文档处理程序的方法，并实现每个特定SOLIDWORKS模型所需的功能（例如处理事件、加载、写入数据等）。

框架将自动释放处理程序。在[Dispose](https://docs.codestack.net/swex/add-in/html/M_CodeStack_SwEx_AddIn_Core_DocumentHandler_Dispose.htm)或[OnDestroy](https://docs.codestack.net/swex/add-in/html/M_CodeStack_SwEx_AddIn_Core_DocumentHandler_OnDestroy.htm)方法中取消订阅自定义事件。与处理程序关联的文档的指针将分配给[Model](https://docs.codestack.net/swex/add-in/html/P_CodeStack_SwEx_AddIn_Core_DocumentHandler_Model.htm)属性。