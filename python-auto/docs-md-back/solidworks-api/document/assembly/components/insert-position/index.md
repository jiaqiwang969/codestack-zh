---
title: Batch add components and position them in the grid using SOLIDWORKS API
caption: Insert And Position Components In A Grid
description: VBA example demonstrates how to batch insert and position components in the 3D grid using SOLIDWORKS API by providing the number of rows and columns and distance between components
image: positioned-components.png
labels: [components,positions]
---
![插入到2 x 2 x 2网格中的组件](positioned-components.png){ width=250 }

此示例演示了使用SOLIDWORKS API将一批组件高效地插入到装配体中，并自动将它们定位在3D网格中的方法。

使用[SOLIDWORKS API的IAssemblyDoc::AddComponents3](https://help.solidworks.com/2011/English/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IAssemblyDoc~AddComponents3.html)方法来插入组件。该方法允许预先分配要插入的组件的变换。

可以通过在宏的开头设置常量来指定网格的边界。

~~~ vb
Const ROWS_COUNT As Integer = 2 '每行（X轴平行）中的最大组件数
Const COLUMNS_COUNT As Integer = 2 '每列（Y轴平行）中的最大组件数
Const DISTANCE As Double = 0.1 '行、列和层之间的距离
~~~

通过为*compsPaths*数组分配值来指定要插入的组件列表。支持在不同位置插入相同的组件路径。

~~~ vb
Dim compsPaths(N) As String
    
compsPaths(0) = "部件或装配体的完整路径"
compsPaths(1) = "部件或装配体的完整路径"
...
compsPaths(N) = "部件或装配体的完整路径"
~~~

{% code-snippet { file-name: Macro.vba } %}