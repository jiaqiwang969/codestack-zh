---
title: Working with dimensions using SOLIDWORKS API
caption: Dimensions
description: Collection of articles and code examples for automating models dimensions via SOLIDWORKS API
order: 7
image: solidworks-dimensions-api.png
---

![通过SOLIDWORKS API自动化尺寸](solidworks-dimensions-api.png){ width=300 }

可以通过[SOLIDWORKS API的IModelDocExtension::AddDimension](https://help.solidworks.com/2022/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeldocextension~adddimension.html)方法将尺寸添加到所选的草图段上。

每个尺寸都有一个用户可以分配的唯一名称。可以通过[IModelDoc2::Parameter](https://help.solidworks.com/2022/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeldoc2~parameter.html)方法按名称检索尺寸对象。

请参考[SOLIDWORKS API接口IDimension](https://help.solidworks.com/2022/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IDimension.html)以获取可用于尺寸自动化的方法列表。