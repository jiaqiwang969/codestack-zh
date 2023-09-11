---
title: Create and display b-spline curve using SOLIDWORKS API
caption: Create B-Spline Curve
description: VBA example demonstrates how to create and preview b-spline curve from the sample data using SOLIDWORKS API
image: bspline-curve-preview.png
labels: [curve, bspline, modeler]
---
![B样条曲线预览](bspline-curve-preview.png){ width=250 }

这个VBA示例演示了如何使用[IModeler::CreateBsplineCurve](https://help.solidworks.com/2012/English/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModeler~CreateBsplineCurve.html)方法根据示例数据创建和预览B样条曲线。

打开零件文档并运行宏。曲线将被预览并且宏停止。继续运行宏以销毁曲线。

请参考[获取B样条曲线参数](/solidworks-api/geometry/get-bspline-parameters/)示例以了解如何从选定的边缘提取所需数据。

{% code-snippet { file-name: Macro.vba } %}