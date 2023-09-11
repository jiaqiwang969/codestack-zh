---
title: Add mate between coordinate systems using SOLIDWORKS API
caption: Add Mate Between Coordinate Systems
description: Macro adds coincident mate between 2 coordinate systems of 2 selected components
image: sw-mate-coincident.png
labels: [assembly, component, coordinate system, example, mate, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-assembly-add-mate-between-coord-sys.html
  - /solidworks-api/document/assembly/add-mate-between-coordinate-systems
---
使用SOLIDWORKS API在两个选定的组件的两个坐标系之间添加一致连接。这些组件必须包含名为*Coordinate System1*的坐标系特征。

![一致连接属性管理器页面](sw-mate-coincident.png){ width=640 }

使用[IAssemblyDoc::AddMate3](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iassemblydoc~addmate3.html) SOLIDWORKS API插入连接特征。

{% code-snippet { file-name: Macro.vba } %}