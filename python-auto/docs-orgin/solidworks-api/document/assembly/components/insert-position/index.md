---
title: Batch add components and position them in the grid using SOLIDWORKS API
caption: Insert And Position Components In A Grid
description: VBA example demonstrates how to batch insert and position components in the 3D grid using SOLIDWORKS API by providing the number of rows and columns and distance between components
image: positioned-components.png
labels: [components,positions]
---
![Components inserted into 2 x 2 x 2 grid](positioned-components.png){ width=250 }

This example demonstrates the performance efficient way of inserting a batch of components into assembly and automatic positioning of them in 3D grid using SOLIDWORKS API.

Components are inserted using the [IAssemblyDoc::AddComponents3](https://help.solidworks.com/2011/English/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IAssemblyDoc~AddComponents3.html) SOLIDWORKS API method. Which allows to preassign the transformations for components to be inserted.

Boundaries of the grid can be specified by setting the constants in the begging of the macro.

~~~ vb
Const ROWS_COUNT As Integer = 2 'maximum number of components in a row (parallel to X)
Const COLUMNS_COUNT As Integer = 2 'maximum number of components in a row (parallel to Y)
Const DISTANCE As Double = 0.1 'distance between components in rows, columns and levels
~~~

Specify the list of components to insert by assigning the values of *compsPaths* array. Inserting the same component path in different positions is supported.

~~~ vb
Dim compsPaths(N) As String
    
compsPaths(0) = "Full path to part or assembly"
compsPaths(1) = "Full path to part or assembly"
...
compsPaths(N) = "Full path to part or assembly"
~~~

{% code-snippet { file-name: Macro.vba } %}
