---
title: 使用宏在SOLIDWORKS中通过API更改系统页面设置选项
caption: 更改系统页面设置选项
description: 使用SOLIDWORKS API更改系统级别（应用程序）的页面设置选项（打印机纸张大小、比例等）以进行打印
image: page-setup.png
labels: [打印,页面设置,偏好设置]
---
![页面设置](page-setup.png){ width=350 }

本示例演示了如何使用SOLIDWORKS API更改系统页面设置选项（纸张大小和比例），并将当前文档选项设置为使用系统设置。

此示例还演示了如何通过指定纸张名称来检索[IPageSetup::PrinterPaperSize](https://help.solidworks.com/2016/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IPageSetup~PrinterPaperSize.html)的系统特定纸张大小整数。

{% code-snippet { file-name: Macro.vba } %}