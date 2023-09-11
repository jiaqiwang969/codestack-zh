---
caption: 重命名尺寸
title: 在SOLIDWORKS绘图视图中重命名尺寸的宏
description: VBA宏允许在SOLIDWORKS绘图视图中为尺寸分配自定义名称，而这些尺寸在用户界面中无法重命名
image: read-only-dimension-name.png
---
SOLIDWORKS允许在3D文档（零件和装配）中分配自定义尺寸名称。

然而，绘图视图中的尺寸名称是只读的，无法更改。

在某些情况下，为绘图视图中的尺寸分配自定义名称可能是有益的。例如，当尺寸是[检验报告](/solidworks-api/document/drawing/export-dimensions/)的一部分或者是DriveWorks等绘图自动化软件的一部分时。

这个VBA宏允许在绘图视图中为尺寸分配自定义名称。

选择要更改名称的尺寸，然后运行宏。

在弹出的对话框中指定新名称。

![无法在用户界面中更改尺寸名称](read-only-dimension-name.png){width=600}

指定名称后，尺寸名称将设置为新值。

![尺寸名称已更改为自定义名称](renamed-dimension.png)

> 还可以以\<尺寸名称\>@\<特征名称\>的格式分配尺寸的完整名称（例如MyDimension@MyView）。在这种情况下，宏还将重命名父视图。这对于无法重命名的视图（例如剖视图）非常有益。

{% code-snippet { file-name: Macro.vba } %}