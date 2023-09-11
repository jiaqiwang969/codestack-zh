---
title: Macro slices body by sections using SOLIDWORKS API
caption: Slice Body By Sections
description: Example demonstrates how to slice body by sections and extract the section data from the slices using SOLIDWORKS API
image: sliced-sections.png
labels: [slice, projection, intersection, modeler, temp body]
---
![实体的截面切片](sliced-sections.png){ width=350 }

本示例演示了如何使用SOLIDWORKS API切割所选实体，并通过SOLIDWORKS API计算切割结果的截面属性。

* 在常量*SLICES_COUNT*中指定所需切片的数量
~~~ vb
Const SLICES_COUNT As Integer = 100
~~~
* 在零件文档中选择实体
* 结果如下：
    * 实体在Y方向上被切割
    * 每个切片的面积将在VBA编辑器的即时窗口中输出
    * 每个切片的预览将显示在图形区域中
* 继续运行宏以隐藏预览

## 算法

### 确定实体的起始点和最大长度

* 找到方向向量（本示例中为Y向量）正方向和负方向上的2个极点
* 将这些点投影到方向向量线上（向量可以固定在任意点，本示例中固定在0, 0, 0）
* 投影后计算两点之间的距离 - 这将等于实体的最大长度
* 第一个极点是起始点

### 确定实体的最大半径
只需要找到足够大的半径以覆盖整个实体。这个半径将用于创建一个平面实体以进行相交计算。在本示例中，最大半径等于包围盒的对角线长度，这将确保平面截面将覆盖输入实体。

### 计算截面
* 计算截面的步长
* 对于每个截面，将起始点按步长移动。末端的截面应该被跳过，因为它不会产生任何相交结果
* 在每个步长处创建一个临时截面平面（圆盘）并将其与实体相交
    * 相交的结果是截面切片的面体（或面体）。将截面的指针存储在集合中
    * 所有属性都可以从结果面体中访问（例如表面积）

### 预览结果
* 将每个结果面体显示为预览
* 停止宏的执行以验证结果
    * 可能需要隐藏或更改原始实体的透明度以查看显示的截面
* 继续宏的执行。这将清除预览

{% code-snippet { file-name: Macro.vba } %}