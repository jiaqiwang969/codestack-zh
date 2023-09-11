---
layout: sw-tool
title: count all selected components using SOLIDWORKS API
caption: Count All Selected Components
description: Macro counts all unique components selected in the assembly and displays the result in the commands bar
image: status-bar-selected-comps.png
labels: [assembly, count components, solidworks api, status bar, utility]
group: Assembly
redirect-from:
  - /2018/03/solidworks-api-assembly-count-selected-components.html
  - /solidworks-api/document/assembly/count-all-selected-components
---
该宏使用SOLIDWORKS API计算所选装配体中所有唯一组件的数量。组件可以在特征管理树或图形区域中选择。

如果仅选择了组件的实体（例如面或边），宏也会计算该组件，使用[SOLIDWORKS API接口ISelectionMgr](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ISelectionMgr.html)。

![所选组件数量显示在状态栏中](status-bar-selected-comps.png){ width=320 }

{% code-snippet { file-name: Macro.vba } %}