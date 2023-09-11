---
title: 通过SwEx.AddIn框架将数据存储在第三方存储（流）中
caption: 流
description: 使用SwEx.AddIn框架将自定义结构序列化到第三方存储（流）中
toc-group-name: labs-solidworks-swex
order: 1
---
调用[IModelDoc2::Access3rdPartyStream](https://docs.codestack.net/swex/add-in/html/M_SolidWorks_Interop_sldworks_ModelDocExtension_Access3rdPartyStream.htm)扩展方法来访问第三方流。传递布尔参数以读取或写入流。

当需要在模型中存储单个结构时，使用此方法。

## 流访问处理程序

为了简化流生命周期的处理，使用SwEx.AddIn框架的Documents Manager API：

{% code-snippet { file-name: ThirdPartyData.StreamHandler.* } %}

## 读取数据

[IThirdPartyStreamHandler::Stream](https://docs.codestack.net/swex/add-in/html/P_CodeStack_SwEx_AddIn_Base_IThirdPartyStreamHandler_Stream.htm)属性在读取不存在的流时返回null。

{% code-snippet { file-name: ThirdPartyData.Stream.StreamLoad.* } %}

## 写入数据

[IThirdPartyStreamHandler::Stream](https://docs.codestack.net/swex/add-in/html/P_CodeStack_SwEx_AddIn_Base_IThirdPartyStreamHandler_Stream.htm)将始终返回指向流的指针（如果流不存在，则会自动创建流）。

{% code-snippet { file-name: ThirdPartyData.Stream.StreamSave.* } %}