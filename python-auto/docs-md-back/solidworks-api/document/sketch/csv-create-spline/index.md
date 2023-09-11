---
title: Macro to create spline CSV file using SOLIDWORKS API
caption: Create Spline From CSV
description: VBA macro to create spline in the active sketch from the points loaded from the CSV file using SOLIDWORKS API
image: spline-pmpage.png
labels: [csv, sketch, spline]
---
![在带有属性管理器页面的草图中的样条曲线](spline-pmpage.png)

这个VBA宏演示了如何通过从CSV文件中加载点数据来创建活动草图中的样条曲线。CSV文件应该包含3列，用于表示样条节点的坐标（以米为单位）。[下载示例样条数据](spline-data.csv)

在**CSV_FILE_PATH**常量中指定该文件的完整路径。

{% code-snippet { file-name: Macro.vba } %}