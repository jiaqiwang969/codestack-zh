---
title: 使用SOLIDWORKS API在配件之间插入管道组件
caption: 插入管道
description: 这是一个用于自动化管道的VBA宏，根据配件的止口面插入管道组件
image: pipe.svg
labels: [管道, 配件, 装配, 管道工程]
---
这个VBA宏在选定的两个配件的止口面之间插入新的虚拟组件到SOLIDWORKS装配中。

![配件的止口面](fitting-stop-face.png){ width=400 }

止口面必须是平面的，带有两个圆形边缘。两个配件之间的边缘必须同心。

宏将执行以下步骤：

* 基于第一个止口面创建新的虚拟组件。
* 在第一个止口面上创建新的草图。
* 将止口面的两个边缘转换为草图。
* 将草图挤压到第二个止口面。
* 根据**MATERIAL_NAME**变量分配材料。
* 关闭虚拟组件。

![两个配件之间的管道](pipe-fittings.png){ width=400 }

结果将创建一个具有可调节内外直径和长度的管道。改变配件的位置或尺寸将自动改变管道的几何形状。

{% code-snippet { file-name: Macro.vba } %}