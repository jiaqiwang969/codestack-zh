---
title: 使用SOLIDWORKS API按类型从绘图中查找表格
caption: 按类型查找表格
description: 使用SOLIDWORKS API从绘图中的图纸中查找所有表格（BOM、通用、修订）。
image: drawing-view-tables.png
labels: [表格, 绘图]
---
![绘图文档中的表格](drawing-view-tables.png){ width=250 }

这个示例使用SOLIDWORKS API从活动绘图文档中按指定类型查找所有表格。

需要使用Array函数指定类型数组，其中每个值表示表格的类型（BOM、通用、切割清单、修订、标题块等），这些类型在[swTableAnnotationType_e](https://help.solidworks.com/2017/english/api/swconst/solidworks.interop.swconst~solidworks.interop.swconst.swtableannotationtype_e.html)枚举中定义。

作为结果，返回指向[ITableAnnotation](https://help.solidworks.com/2017/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ITableAnnotation.html) SOLIDWORKS API接口的指针数组，并将每个表格的标题输出到VBA编辑器的即时窗口。

{% code-snippet { file-name: Macro.vba } %}