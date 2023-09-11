---
caption: Find And Read Table By Cell
title: Find and read the table in the SOLIDWORKS drawing by the value of the cell
description: VBA macro to find the table in the SOLIDWORKS drawing by the value in the specified cell and reading its data into the variable
image: general-table.png
---
这个VBA宏通过指定单元格中的值模式来查找表格。

![图纸中的通用表格](general-table.png){ width=500 }

表格的数据被读取到字符串变量**tableData**中，并输出到[VBA即时窗口](/visual-basic/vba/vba-editor/windows#immediate-window)中。

单元格之间使用**DELIMETER**常量的值进行分隔。

可以使用匹配模式来匹配单元格的值（例如**\*ABC\***将匹配包含**ABC**的文本）

文本比较不区分大小写。

要搜索的行和列的索引是从0开始的（例如第一列中的第一个单元格的索引为**0, 0**）。

在调用**FindTableByContent**函数时，提供搜索模式的值和目标单元格的位置。

~~~ vb jagged
Set swTableAnnotation = FindTableByContent(swDraw, "*ABC*", 0, 0)
~~~

![即时窗口中的表格数据输出](immediate-window-output.png)

{% code-snippet { file-name: Macro.vba } %}