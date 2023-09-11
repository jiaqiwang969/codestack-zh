---
title: SOLIDWORKS宏以更改模式中组件的配置特定属性
caption: 更改模式中组件的配置特定属性
description: 本示例演示了如何使用SOLIDWORKS API更改模式中组件的配置特定属性（使用与模式种子组件相同的配置或使用命名配置）
image: component-config-specific-properties.png
labels: [装配体, 模式, 配置, 种子]
---
![草图驱动模式的种子组件的配置特定属性](component-config-specific-properties.png)

此宏示例演示了如何使用SOLIDWORKS API更改以下配置特定属性。

* 使用与模式种子组件相同的配置
* 使用命名配置

使用[IAssemblyDoc::CompConfigProperties5](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iassemblydoc~compconfigproperties5.html) SOLIDWORKS API可以一次修改所选组件的多个属性。

在模式的实例组件中（例如，草图驱动模式）

{% code-snippet { file-name: Macro.vba } %}