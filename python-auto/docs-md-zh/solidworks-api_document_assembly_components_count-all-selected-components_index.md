---
layout: sw-tool
title: 使用SOLIDWORKS API计算所有选定组件的数量
caption: 计算所有选定组件的数量
description: 该宏使用SOLIDWORKS API计算选定装配体中所有唯一组件的数量，并在命令栏中显示结果
image: status-bar-selected-comps.png
labels: [装配体, 计算组件, SOLIDWORKS API, 状态栏, 实用工具]
group: 装配体
redirect-from:
  - /2018/03/solidworks-api-assembly-count-selected-components.html
  - /solidworks-api/document/assembly/count-all-selected-components
---
该宏使用SOLIDWORKS API计算选定装配体中所有唯一组件的数量。组件可以在特征管理树或图形区域中进行选择。

如果仅选择了组件的实体（例如面或边），宏也会计算该组件的数量，使用[SOLIDWORKS API接口](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ISelectionMgr.html)的[ISelectionMgr](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ISelectionMgr.html)。

![在状态栏中显示选定组件的数量](status-bar-selected-comps.png){ width=320 }

{% code-snippet { file-name: Macro.vba } %}