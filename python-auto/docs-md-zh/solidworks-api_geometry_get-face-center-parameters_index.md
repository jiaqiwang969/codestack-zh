---
title: 使用SOLIDWORKS API获取面的质心参数
caption: 获取面质心参数
description: 本示例演示了如何使用SOLIDWORKS API在面的质心处找到面参数（坐标和法线）
image: face-center.png
labels: [质心, UV, 法线]
---
![在面的质心处创建的点](face-center.png){ width=250 }

本示例演示了如何使用SOLIDWORKS API在面的质心处找到参数（点坐标和法线）。该宏适用于任何类型的面（平面、圆柱面、环面、B曲面等）。

通过使用[SOLIDWORKS API的ISurface::Evaluate](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isurface~evaluate.html)方法，质心被定义为U和V参数的最小值和最大值的平均值。

{% code-snippet { file-name: Macro.vba } %}