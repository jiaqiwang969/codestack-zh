---
title: Change system page setup options in SOLIDWORKS using API in macro
caption: Change System Page Setup Options
description: Changing system level (application) page setup options (printer paper size, scale, etc.) for printing using SOLIDWORKS API
image: page-setup.png
labels: [print,page setup,preferences]
---
![页面设置](page-setup.png){ width=350 }

本示例演示了如何使用SOLIDWORKS API更改系统页面设置选项（纸张大小和比例），并将当前文档选项设置为使用系统设置。

此示例还演示了如何通过指定纸张名称来检索[IPageSetup::PrinterPaperSize](https://help.solidworks.com/2016/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IPageSetup~PrinterPaperSize.html)的系统特定纸张大小整数。

{% code-snippet { file-name: Macro.vba } %}