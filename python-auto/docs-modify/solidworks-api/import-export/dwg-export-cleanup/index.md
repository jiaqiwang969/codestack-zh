---
title: Export Flat Pattern to DXF/DWG with Cleanup page using SOLIDWORKS API
caption: Export Flat Pattern With Cleanup
description: VBA example which demonstrates how to export specified flat pattern to DXF/DWG with Cleanup dialog
image: cleanup-page.png
labels: [dxf,dwg,cleanup,flat pattern,export]
---
[SOLIDWORKS API方法IPartDoc::ExportToDwg2](https://help.solidworks.com/2014/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IPartDoc~ExportToDWG2.html)允许将选定的平面图案导出为DXF/DWG格式。但是该API不允许在导出之前显示内置的清理对话框以修改DXF/DWG。

![DXF/DWG 清理](cleanup-page.png){ width=350 }

下面的代码提供了解决此问题的方法。

> 注意：此代码不允许设置导出的设置（使用默认选项）。需要使用Windows API来修改选项和复选框。

## 配置

按照下面的示例指定宏参数：

~~~vb
Const FLAT_PATTERN_FEAT_NAME As String = "Flat-Pattern1" '要导出的平面图案特征的名称
Const OUT_FILE_NAME As String = "D:\sample.dxf" '导出的输出文件名
~~~

## 宏模块

{% code-snippet { file-name: Macro.vba } %}

## ExportEventsListener 类模块

创建一个名为**ExportEventsListener**的新[类模块](/visual-basic/classes/)，并添加下面的代码

{% code-snippet { file-name: ExportEventsListener.vba } %}