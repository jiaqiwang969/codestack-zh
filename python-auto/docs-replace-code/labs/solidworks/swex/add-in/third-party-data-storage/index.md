---
title: Storing 3rd party data in SOLIDWORKS models using SwEx.AddIn framework
caption: 3rd Party Data Storage
description: Storing 3rd party data (structures and storages) in SOLIDWORKS model stream using SwEx.AddIn framework
toc-group-name: labs-solidworks-swex
order: 5
---
SwEx.AddIn框架提供了在SOLIDWORKS第三方存储（流）和存储库中处理数据（序列化和反序列化）的功能。

请参考[SOLIDWORKS API中的第三方存储数据保存](/solidworks-api/data-storage/third-party/)，了解第三方存储和存储库的详细概述。

建议与[文档管理](/labs/solidworks/swex/add-in/documents-management/)功能一起使用此功能，通过重写[OnLoadFromStream](https://docs.codestack.net/swex/add-in/html/M_CodeStack_SwEx_AddIn_Core_DocumentHandler_OnLoadFromStream.htm)、[OnSaveToStream](https://docs.codestack.net/swex/add-in/html/M_CodeStack_SwEx_AddIn_Core_DocumentHandler_OnSaveToStream.htm)、[OnLoadFromStorageStore](https://docs.codestack.net/swex/add-in/html/M_CodeStack_SwEx_AddIn_Core_DocumentHandler_OnLoadFromStorageStore.htm)、[OnSaveToStorageStore](https://docs.codestack.net/swex/add-in/html/M_CodeStack_SwEx_AddIn_Core_DocumentHandler_OnSaveToStorageStore.htm)方法。

观看使用SwEx.AddIn框架存储第三方数据的短视频演示：

{% youtube { id: 9Y_OsoauvuQ } %}