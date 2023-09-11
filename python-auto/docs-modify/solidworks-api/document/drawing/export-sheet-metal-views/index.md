---
layout: sw-tool
title: Export flat pattern view in the drawing using VBA macro
caption: Export Flat Patterns
description: VBA macro to export flat pattern views in the drawing active sheet to DXF or DWG or other format preserving the bend notes, annotations etc. using SOLIDWORKS API
image: flat-pattern-view.png
labels: [dxf,dwg,export,flat pattern]
group: Drawing
---
![展开图导出为DXF](flat-pattern-dxf.png){ width=350 }

此VBA宏使用SOLIDWORKS API，将绘图活动工作表中的所有展开图视图导出为指定格式（如DXF或DWG）。宏将文件导出到与原始绘图相同的文件夹，并以绘图视图名称命名文件。

如果需要将导出的文件命名为切割清单名称，可以与[使用切割清单名称重命名展开图视图](/solidworks-api/document/drawing/rename-sheet-metal-views/)宏一起使用。

在宏的开头指定输出文件扩展名：

~~~ vb
Const OUT_EXT As String = ".dxf"
~~~

## 算法

* 遍历当前绘图活动工作表的所有绘图视图
* 查找所有展开图绘图视图
* 创建新的临时绘图并复制视图
* 删除所有尺寸
* 删除所有表格
* 将视图和工作表比例设置为1:1
* 将工作表尺寸调整为视图大小
* 导出到指定文件


{% code-snippet { file-name: Macro.vba } %}