---
title: 使用SOLIDWORKS API移动设计表对象
caption: 移动设计表OLE对象
description: 本示例演示了如何使用SOLIDWORKS API方法调整和移动模型图形区域中的设计表OLE对象的大小和位置。
image: design-table-ole-object.png
labels: [装饰, 边界, 设计表, 示例, 移动, OLE对象, SOLIDWORKS API]
redirect-from:
  - /2018/03/move-design-table-ole-object.html
---
本示例演示了如何使用[SOLIDWORKS API方法ISwOLEObject::Boundaries](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iswoleobject~boundaries.html)调整和移动模型图形区域中的设计表OLE对象的大小和位置。

![模型图形区域中的设计表OLE对象](design-table-ole-object.png){ width=640 height=226 }

在本示例中，将把现有的设计表元素向右移动，移动距离等于对象的宽度。

{% code-snippet { file-name: Macro.vba } %}