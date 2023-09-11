---
title: SOLIDWORKS macro finds intersection points between surface and curve
caption: Find Intersection Points Between Surface And Curve
description: Example demonstrates how to find the intersection points between selected plane or face with edge or sketch segment
image: surface-curve-intersection.png
labels: [curve, evaluate, geometry, macro, points, solidworks api, spline, intersection, trimmed curve, vba]
---
![平面和草图样条线之间的交点](surface-curve-intersection.png){ width=300 }

该示例演示了如何使用SOLIDWORKS API找到所选曲面（平面或面）与曲线（边缘或草图段）之间的交点。

* 打开零件文档
* 选择平面或任何面作为第一个选择对象
* 选择草图段（线段、样条线或弧）作为第二个选择对象
* 运行宏。结果将创建一个包含所选对象之间交点的3D草图。

[ISurface::IntersectCurve2](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isurface~intersectcurve2.html) 是SOLIDWORKS API中用于在曲线和曲面的指定边界内查找交点的方法。

{% code-snippet { file-name: Macro.vba } %}