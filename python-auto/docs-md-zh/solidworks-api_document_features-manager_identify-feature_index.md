---
layout: sw-tool
title: 识别SOLIDWORKS API功能定义和特定类型
caption: 识别功能定义和特定类型
description: 通过SOLIDWORKS API和反射，提供帮助方法来识别所选功能的定义和特定类型
image: specific-feature-types.png
labels: [反射, 特定功能, 功能定义]
group: 开发人员
---
![将特定功能和功能定义的类型输出到窗口](specific-feature-types.png){ width=450 }

[IFeature::GetSpecificFeature2](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IFeature~GetSpecificFeature2.html)和[IFeature::GetDefinition](https://help.solidworks.com/2012/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ifeature~getdefinition.html) SOLIDWORKS API方法返回的分派指针在某些情况下不容易识别和转换为特定类型。

以下代码示例允许输出所选功能的定义和特定功能的所有可分配接口。结果将输出到VSTA编辑器的“输出”窗口中。

{% code-snippet { file-name: Macro.cs } %}