---
layout: sw-tool
title: 从SOLIDWORKS图纸中导出单独的工作表到PDF
caption: 导出工作表到PDF
description: VBA宏，将多工作表图纸中的所有工作表（或选定的工作表）导出为单独的PDF文件
image: exports-sheets-pdf.svg
labels: [工作表, PDF, 图纸, 导出]
group: 导入/导出
---
![多工作表图纸](drawing-multi-sheets.png){ width=500 }

这个VBA宏允许将活动的SOLIDWORKS图纸中的所有工作表（或选定的工作表）导出为单独的PDF文件。如果没有选择工作表，则会导出所有工作表。

PDF文件保存在与原始图纸相同的文件夹中，并以工作表的名称命名。

*INCLUDE_DRAWING_NAME*选项允许在输出PDF中包含图纸的名称，如果设置为*True*，否则只使用工作表的名称。

~~~ vb jagged-bottom
Const INCLUDE_DRAWING_NAME As Boolean = True '包含图纸的名称
~~~

{% code-snippet { file-name: Macro.vba } %}