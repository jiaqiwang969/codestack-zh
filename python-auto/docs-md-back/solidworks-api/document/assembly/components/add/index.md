---
title: Add components to assembly using SOLIDWORKS API
caption: Add Components To Assembly
description: Example Demonstrates 2 different ways to add component into the assembly tree (single component add or batch adding)
labels: [add component, assembly, example, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-assembly-add-components.html
  - /solidworks-api/document/assembly/add-components
---
该示例演示了使用SOLIDWORKS API将组件添加到装配体树中的两种不同方法。

* 传统的方式是通过[SOLIDWORKS API的AddComponentX](https://help.solidworks.com/2015/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IAssemblyDoc~AddComponent5.html)来添加组件，该方法需要将模型加载到内存中。否则，操作将失败。
* 更高级的方式是使用[SOLIDWORKS API的AddComponents](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IAssemblyDoc~AddComponents3.html)。该方法允许在不预先打开模型的情况下批量插入不同的组件。

[下载示例文件](parts.zip)

{% code-snippet { file-name: Macro.vba } %}