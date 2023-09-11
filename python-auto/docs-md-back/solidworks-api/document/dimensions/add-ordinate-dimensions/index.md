---
caption: Add Holes Ordinate Dimensions
title: Macro to add horizontal and vertical ordinate dimensions for holes in SOLIDWORKS drawings view
description: SOLIDWORKS VBA macro to add horizontal and vertical ordinate dimensions for all holes of the selected view relative to the bottom left vertex 
image: ordinate-dimensions.png
---
![图纸视图中的纵坐标尺寸](ordinate-dimensions.png)

这个SOLIDWORKS VBA宏可以自动为所选图纸视图中的所有孔洞添加水平纵坐标尺寸。

* 宏将通过找到视图中的左下顶点来确定纵坐标尺寸的起点
* 宏将找到视图中的所有孔洞（仅包括内部孔洞，不考虑倒角）
* 宏将为孔洞添加水平和垂直尺寸
* 尺寸将相对于图纸视图进行定位

{% code-snippet { file-name: Macro.vba } %}