---
title: 使用SOLIDWORKS API找到物体的包围圆柱体
caption: 获取物体的包围圆柱体
description: 本示例演示了如何使用SOLIDWORKS API获取实体物体的包围圆柱体。
image: cylindrical-bounding-box.png
---
![围绕物体创建的圆柱体边界框](cylindrical-bounding-box.png){ width=400 }

本示例演示了如何使用SOLIDWORKS API找到实体物体的包围圆柱体。

宏要求用户选择输入参数以确定圆柱体的方向。用户可以选择圆形面（在这种情况下，轴将被用作参考）或平面特征（在这种情况下，法线将被用作参考）。

结果将创建一个新的特征，表示物体的圆柱边界。

> 该宏将为任意方向的物体创建最佳拟合的包围圆柱体。物体不一定需要与XYZ轴对齐。

可以在[此链接](GetBoundingCylinderBin.zip)下载宏。解压缩宏并从“工具”->“宏”->“运行”菜单命令中运行它。如下所示指定正确的过滤器：

![从SOLIDWORKS运行VSTA宏](run-vsta-macro.png){ width=500 }

### SolidWorksMacro.cs
这是VSTA宏的入口点。在此模块中处理输入参数并创建输出物体。
{% code-snippet { file-name: SolidWorksMacro.cs } %}

### CylinderParams.cs
此结构表示包围圆柱体的详细信息。
{% code-snippet { file-name: CylinderParams.cs } %}

### BodyHelper.cs
此实用类允许找到物体的方向并将其适配到圆柱体中。
{% code-snippet { file-name: BodyHelper.cs } %}

### MathHelper.cs
此模块提供用于处理向量、变换和点的实用函数。
{% code-snippet { file-name: MathHelper.cs } %}

此宏需要引用Project Nayuki的[Smallest enclosing circle - Library (C#)](https://www.nayuki.io/page/smallest-enclosing-circle)。