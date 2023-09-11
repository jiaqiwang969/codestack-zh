---
layout: sw-macro-fix
title: 修复SOLIDWORKS宏在装配或绘图中使用轻量级组件的问题
caption: 装配或绘图中的轻量级组件
description: 修复宏在处理装配中的组件时出现的运行时错误'91' - 对象变量或With块变量未设置
image: lightweight-component.png
labels: [宏, 故障排除]
redirect-from:
  - /2018/04/宏故障排除装配中的轻量级组件.html
---
## 症状

SOLIDWORKS宏在处理装配中的组件（例如读取/写入属性、材料、处理特征等）时出现问题。
运行宏时显示错误*运行时错误'91'：对象变量或With块变量未设置*。

## 原因

组件可以以轻量级加载，这意味着它们的底层模型未加载到内存中。
在这种情况下，组件模型的所有API都不可用。

![特征管理器树中的轻量级组件](lightweight-component.png)

## 解决方法

* 检查引用模型的指针是否不为空。向用户显示错误消息。
* 使用[AssemblyDoc::ResolveAllLightWeightComponents](https://help.solidworks.com/2016/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iassemblydoc~resolvealllightweightcomponents.html)或[AssemblyDoc::ResolveAllLightWeight](https://help.solidworks.com/2016/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IAssemblyDoc~ResolveAllLightweight.html)方法强制解决组件状态

{% code-snippet { file-name: get-selected-component-material.vba } %}