---
layout: sw-macro-fix
title: Fixing the inconsistent selections in the SOLIDWORKS macro
caption: Selections are inconsistent in the macro
description: Fixing the error when selections in the macro are not consistent
image: recorded-macro-extrude.png
labels: [macro, troubleshooting]
---
## 症状

使用[宏录制工具](https://help.solidworks.com/2012/english/solidworks/sldworks/c_recording_playing_macros.htm)录制的SOLIDWORKS宏需要进行一些选择（通常用于创建特征或配对）。运行宏时，选择可能失败，或选择了不同的对象，导致宏行为异常。

## 原因

通常，宏录制使用[SOLIDWORKS API](https://help.solidworks.com/2012/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeldocextension~selectbyid2.html)中的[IModelDocExtension::SelectByID2](https://help.solidworks.com/2012/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeldocextension~selectbyid2.html)方法来捕获选择。该方法可能使用临时名称（如草图段名称）或坐标进行选择，这些在不同模型或视图方向上可能不一致。

![通过名称选择草图中的弧的录制宏行](recorded-macro-extrude.png){ width=500 }

## 解决方法

更新选择方法。详细指南请参考[选择](solidworks-api/document/selection)文章。