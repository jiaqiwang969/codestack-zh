---
title: Importing and exporting files using SOLIDWORKS API
caption: Import/Export
description: Collection of examples and articles related to files importing and exporting using SOLIDWORKS API
image: import-export.svg
order: 7
---
![使用SOLIDWORKS API导入和导出SOLIDWORKS文件](import-export.svg){ width=250 }

SOLIDWORKS API允许通过[IModelDocExtension::SaveAs2](https://help.solidworks.com/2019/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeldocextension~saveas2.html)将文件导出为外部格式，只需指定外部文件的相应扩展名（例如stp、x_t、igs等）。

要导入外部文件，需要使用[ISldWorks::LoadFile4](https://help.solidworks.com/2019/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~loadfile4.html) SOLIDWORKS API方法。该函数的参数允许指定额外的导入选项。

本节包含用于自动化导入和导出SOLIDWORKS功能的代码示例、宏和脚本。