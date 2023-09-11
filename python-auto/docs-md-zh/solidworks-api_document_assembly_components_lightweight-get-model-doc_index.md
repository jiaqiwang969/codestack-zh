---
title: 使用SOLIDWORKS API从轻量级组件获取模型文档
caption: 从轻量级组件获取模型文档
description: 本示例演示了如何使用SOLIDWORKS API从组件中获取到IModelDoc2指针（即使组件处于抑制或轻量级状态）
image: lightweight-component.png
labels: [装配, 组件, 示例, 轻量级, 模型文档, 内存, SOLIDWORKS API]
---
![装配树中的轻量级组件](lightweight-component.png)

[IComponent2::GetModelDoc2](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IComponent2~GetModelDoc2.html) 是SOLIDWORKS API的方法，它返回指向[IModelDoc2](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelDoc2.html)接口的指针。

需要使用该接口来检索模型特定信息（如自定义属性、特征树、注释等）。

对于以轻量级或抑制状态加载的组件，模型文档是不可用的（即指针为*NULL*）。

以下示例演示了如何使用SOLIDWORKS API从组件中获取到IModelDoc2指针（即使组件处于抑制或轻量级状态）。通过直接将组件加载到内存中，无需解析组件或在其自己的窗口中打开文件，即可实现该结果。

{% code-snippet { file-name: Macro.vba } %}