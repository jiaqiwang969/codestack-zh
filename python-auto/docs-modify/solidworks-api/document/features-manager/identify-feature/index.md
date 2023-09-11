---
layout: sw-tool
title: Identify SOLIDWORKS API feature definition and specific type
caption: Identify Feature Definition And Specific Type
description: Helper methods allowing to identify the definition and specific type of the selected feature via SOLIDWORKS API and reflection
image: specific-feature-types.png
labels: [reflection, specific feature, feature definition]
group: Developers
---
![将特定功能和功能定义的类型输出到窗口](specific-feature-types.png){ width=450 }

[IFeature::GetSpecificFeature2](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IFeature~GetSpecificFeature2.html)和[IFeature::GetDefinition](https://help.solidworks.com/2012/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ifeature~getdefinition.html) SOLIDWORKS API方法返回的分派指针在某些情况下不容易识别和转换为特定类型。

以下代码示例允许输出所选功能的定义和特定功能的所有可分配接口。结果将输出到VSTA编辑器的“输出”窗口中。

{% code-snippet { file-name: Macro.cs } %}