---
layout: sw-tool
title: Export dimensions information from SOLIDWORKS drawing to CSV file
caption: Export Dimensions Information
description: VBA macro to export dimensions information (name, position, location, zone, value, tolerance) from SOLIDWORKS drawing to the CSV file
image: export-dimensions.svg
labels: [dimensions,tolerance,export,csv]
group: Drawing
---
![图纸视图中的尺寸](drawing-view.png)

这个VBA宏允许将活动图纸中的所有尺寸信息导出到CSV文件中，该文件可以用Excel打开。

宏将以下信息包含在报告中：

* 名称 - 尺寸的完整名称
* 所属者 - 尺寸所属的图纸视图或图纸页的名称
* 类型 - 尺寸的类型（例如线性、角度、坐标等）
* X - 尺寸在当前图纸单位中的X位置
* Y - 尺寸在当前图纸单位中的Y位置
* 值 - 尺寸的值（当前单位）
* 网格参考 - 尺寸在图纸网格中的参考（例如A5）
* 公差 - 分配给该尺寸的公差类型（例如基本、对称等）
* 最小值 - 公差的最小值（当前单位）
* 最大值 - 公差的最大值（当前单位）

![在Excel中打开的尺寸信息](dimensions-report.png){ width=600 }

输出文件保存在与原始图纸相同的文件夹中，命名为*[图纸名称]-dimensions.csv*

{% code-snippet { file-name: Macro.vba } %}