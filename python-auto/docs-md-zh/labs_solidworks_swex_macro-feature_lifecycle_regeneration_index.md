---
title: SOLIDWORKS宏特征的再生成方法处理
caption: 再生成
description: 使用SwEx.MacroFeature框架处理SOLIDWORKS宏特征的再生成事件，并返回实体或错误以驱动行为
toc-group-name: 实验室-SOLIDWORKS-SwEx
order: 1
---
当特征正在重新构建时（无论是调用再生成还是父元素已更改），将调用此处理程序。

使用[MacroFeatureRebuildResult](https://docs.codestack.net/swex/macro-feature/html/T_CodeStack_SwEx_MacroFeature_Base_MacroFeatureRebuildResult.htm)类生成所需的输出。

特征可以生成以下输出

{% code-snippet { file-name: RegenerationResults.cs } %}

如果特征需要创建新实体，请使用[IModeler](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeler.html)接口。只能从再生成方法返回临时实体。

使用[IModelerExtension](https://docs.codestack.net/swex/macro-feature/html/T_SolidWorks_Interop_sldworks_ModelerEx.htm)类中提供的扩展方法。