---
layout: sw-tool
title: 将SOLIDWORKS文件中选定的草图导出为DXF/DWG文件的宏
caption: 导出草图至DXF/DWG
description: VBA宏，将SOLIDWORKS零件或装配文件中选定的2D草图导出为DXF或DWG文件
image: dxf-sketch.svg
labels: [草图,导出,DXF,DWG]
group: 导入/导出
---
![从草图创建的DXF/DWG文件](sketch-dwf-dwg.png){ width=350 }

此VBA宏将零件或装配中选定的2D草图导出为DXF或DWG文件。

## 选项

通过修改以下示例中的*EXPORT_NAME_TEMPLATE*常量来配置输出文件的名称，使用自由文本和占位符。

* \[title\]占位符将被替换为原始零件或装配文件的标题（不包括扩展名）
* \[sketch\]占位符将被替换为从中创建的草图DXF\DWG文件的名称

在文件模板中指定扩展名（.dxf或.dwg）

文件将保存在与原始零件或装配文档相同的目录中。

~~~ vb
Const EXPORT_NAME_TEMPLATE As String = "ExportFile_[title]_[sketch].dxf"
~~~

{% code-snippet { file-name: Macro.vba } %}