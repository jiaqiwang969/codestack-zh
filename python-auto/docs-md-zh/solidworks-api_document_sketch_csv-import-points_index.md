---
layout: sw-tool
title: 通过SOLIDWORKS API从CSV文件导入点云到草图
caption: 从CSV文件导入点云到草图
description: 该宏使用SOLIDWORKS API将指定CSV文件中的点云导入到活动的2D或3D草图中
image: import-points.svg
labels: [csv, 点云, 草图, 导入]
group: 草图
---
![草图中的点云](points-cloud.png)

该宏使用SOLIDWORKS API从指定的CSV（逗号分隔值）文件中读取点，并将其导入到活动草图中。支持2D和3D草图。

## 配置

宏有几个配置选项，可以通过更改宏开头的常量值来修改。

~~~ vb
Const USE_SYSTEM_UNITS As Boolean = True
Const FIRST_ROW_HEADER As Boolean = True
~~~

* **FIRST_ROW_HEADER** 指定CSV文件的第一行是否被视为标题并应该被忽略。如果CSV文件不包含标题，请将该常量的值设置为**False**。
* **USE_SYSTEM_UNITS** 指示CSV文件中的坐标值是否以系统单位（米）表示。如果将此选项设置为**False**，宏将使用当前文档单位。
* 宏还可以导入相对于坐标系的点。在运行宏之前，请预先选择目标坐标系，否则点将相对于全局坐标系插入。

> 输入的CSV文件可以包含3个坐标（X、Y、Z）或2个坐标（X、Y）。

## 示例文件

* [示例2D点云CSV文件](points-2d.csv)
* [示例3D点云CSV文件](points-3d.csv)

## 如何运行宏

* 打开模型并创建2D或3D草图（或编辑现有草图）
* （可选）如果需要将点导入到相对于该系统的坐标系中，请预先选择坐标系
* 运行宏。在显示的文件浏览对话框中指定CSV文件的完整路径
* 点击确定。点将在活动草图中创建

{% code-snippet { file-name: Macro.vba } %}