---
title: 通过SwEx.AddIn框架将数据存储在第三方存储中
caption: 存储
description: 使用SwEx.AddIn框架将自定义结构序列化到第三方存储中
toc-group-name: labs-solidworks-swex
order: 2
---
调用[IModelDoc2::Access3rdPartyStorageStore](https://docs.codestack.net/swex/add-in/html/M_SolidWorks_Interop_sldworks_ModelDocExtension_Access3rdPartyStorageStore.htm)扩展方法来访问第三方存储。传递布尔参数以读取或写入存储。

当需要存储多个需要独立访问和管理的数据结构时，请使用此方法。与创建多个[流](/labs/solidworks/swex/add-in/third-party-data-storage/stream/)相比，更推荐使用此方法。

## 存储访问处理程序

为了简化存储生命周期的处理，使用SwEx.AddIn框架的Documents Manager API：

{% code-snippet { file-name: ThirdPartyData.StorageHandler.* } %}

## 读取数据

[IThirdPartyStoreHandler::Storage](https://docs.codestack.net/swex/add-in/html/P_CodeStack_SwEx_AddIn_Base_IThirdPartyStoreHandler_Storage.htm)属性在读取不存在的存储时返回null。

{% code-snippet { file-name: ThirdPartyData.Storage.StorageLoad.* } %}

## 写入数据

[IThirdPartyStoreHandler::Storage](https://docs.codestack.net/swex/add-in/html/P_CodeStack_SwEx_AddIn_Base_IThirdPartyStoreHandler_Storage.htm)总是返回指向存储的指针（如果不存在，则自动创建流）。

{% code-snippet { file-name: ThirdPartyData.Storage.StorageSave.* } %}

探索[IComStorage](https://docs.codestack.net/swex/add-in/html/T_CodeStack_SwEx_AddIn_Base_IComStorage.htm)的方法，了解如何创建子流或子存储以及枚举现有元素的信息。