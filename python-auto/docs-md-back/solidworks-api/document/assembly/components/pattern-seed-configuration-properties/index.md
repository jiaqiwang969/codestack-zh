---
title: SOLIDWORKS macro to change configuration specific properties for component in pattern
caption: Change Configuration Specific Properties For Component In Pattern
description: Example demonstrates how to change the configuration specific properties (use same configuration as pattern seed component or use named configuration) of the component in the pattern using SOLIDWORKS API
image: component-config-specific-properties.png
labels: [assembly, spattern, configuration, seed]
---
![草图驱动模式的种子组件的配置特定属性](component-config-specific-properties.png)

此宏示例演示了如何使用SOLIDWORKS API更改以下配置特定属性。

* 使用与模式种子组件相同的配置
* 使用命名配置

使用[IAssemblyDoc::CompConfigProperties5](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iassemblydoc~compconfigproperties5.html) SOLIDWORKS API可以一次修改所选组件的多个属性。

在模式的实例组件中（例如，草图驱动模式）

{% code-snippet { file-name: Macro.vba } %}