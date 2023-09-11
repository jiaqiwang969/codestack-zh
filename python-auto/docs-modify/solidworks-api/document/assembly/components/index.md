---
title: Assembly components automation using SOLIDWORKS API
caption: Components
description: Collection of articles and code examples for working with components in SOLIDWORKS assembly
labels: [assembly, components]
order: 1
---
在SOLIDWORKS装配中，组件是装配中模型文档（[IModelDoc2](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelDoc2.html)）的实例。

可以通过SOLIDWORKS API中的[IComponent2](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IComponent2.html)接口来自动化组件。

对组件的主要操作包括但不限于：

* 变换
* 配合
* 上下文编辑
* BOM组成

可以通过[SOLIDWORKS API的IComponent2::GetModelDoc2](https://help.solidworks.com/2012/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.icomponent2~getmodeldoc2.html)方法获取组件的底层文档的指针。对于被抑制或轻量化的组件，此方法返回null。请参考[获取轻量化组件的模型文档](/solidworks-api/document/assembly/components/lightweight-get-model-doc/)中的代码示例，了解如何获取所有类型组件的指针。

浏览本节以获取关于自动化装配和组件的代码示例和宏。