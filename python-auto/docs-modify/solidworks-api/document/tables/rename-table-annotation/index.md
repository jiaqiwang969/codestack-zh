---
title: Macro renames table annotation using SOLIDWORKS API
caption: Rename Table Annotation
description: Example demonstrates how to rename the selected table using SOLIDWORKS API
image: rename-table-annotation.png
labels: [table, rename]
---
![表格注释已重命名为自定义名称](rename-table-annotation.png){ width=450 }

本示例演示了如何使用SOLIDWORKS API通过[ITableAnnotation](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ITableAnnotation.html)接口重命名所选表格。表格应在图形区域中选择（而不是在特征树中选择）。

通过修改宏的开头处的常量来指定表格的名称：

~~~ vb
Const TABLE_NAME As String = "MyTable"
~~~

{% code-snippet { file-name: Macro.vba } %}