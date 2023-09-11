---
title: 使用SOLIDWORKS API批量添加组件并将其定位在网格中
caption: 在网格中插入和定位组件
description: 此VBA示例演示了如何使用SOLIDWORKS API批量插入和定位组件到3D网格中，通过提供行数、列数和组件之间的距离来实现。
image: positioned-components.png
labels: [组件,定位]
---
![插入到2 x 2 x 2网格中的组件](positioned-components.png){ width=250 }

此示例演示了使用SOLIDWORKS API将一批组件高效地插入到装配体中，并自动将它们定位在3D网格中的方法。

使用[SOLIDWORKS API的IAssemblyDoc::AddComponents3](https://help.solidworks.com/2011/English/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IAssemblyDoc~AddComponents3.html)方法来插入组件。该方法允许预先分配要插入的组件的变换。

可以通过在宏的开头设置常量来指定网格的边界。

~~~ vb
Const ROWS_COUNT As Integer = 2 '每行（沿X轴）中的最大组件数
Const COLUMNS_COUNT As Integer = 2 '每列（沿Y轴）中的最大组件数
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