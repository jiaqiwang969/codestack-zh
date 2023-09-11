---
layout: sw-tool
title: 通过SOLIDWORKS API将组件位置导出为CSV的VBA宏
caption: 导出组件位置
description: 该宏使用SOLIDWORKS API将组件的位置导出到外部CSV文本文件中
image: components-positions-table.png
labels: [导出,CSV,Excel,原点]
group: 装配
---
![在Excel中导出的组件位置](components-positions-table.png){ width=350 }

该宏使用SOLIDWORKS API将活动装配中的组件位置（X、Y、Z）导出到逗号分隔值（CSV）文件中。该文件可以在Excel或任何文本编辑器中打开。

组件位置是相对于装配原点的原点坐标（0, 0, 0）。

宏可以导出所有组件或仅导出所选组件的实例。

* 通过*OUT_FILE_PATH*常量指定输出文件的路径

~~~ vb
Const OUT_FILE_PATH As String = "D:\locations.csv"
~~~

* 通过*CONV_FACTOR*常量指定坐标的米转换因子

~~~ vb
Const CONV_FACTOR As Double = 1000 '米转毫米
~~~

* 可选择选择要仅导出其实例的组件（即具有相同文件路径和引用配置的所有组件）。清除选择以导出所有组件。

结果将创建一个包含以下内容的CSV文件：

* 组件文件完整路径
* 引用的配置
* 组件名称
* 指定单位中原点的X、Y、Z坐标

{% code-snippet { file-name: Macro.vba } %}