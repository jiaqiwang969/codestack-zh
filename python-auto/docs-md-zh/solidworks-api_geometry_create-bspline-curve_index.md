---
title: 使用SOLIDWORKS API创建和显示B样条曲线
caption: 创建B样条曲线
description: VBA示例演示了如何使用SOLIDWORKS API从示例数据创建和预览B样条曲线
image: bspline-curve-preview.png
labels: [曲线, B样条, 建模]
---
![B样条曲线预览](bspline-curve-preview.png){ width=250 }

这个VBA示例演示了使用[IModeler::CreateBsplineCurve](https://help.solidworks.com/2012/English/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModeler~CreateBsplineCurve.html)方法从示例数据创建和预览B样条曲线。

打开零件文档并运行宏。曲线将被预览并停止宏。继续运行宏以处理曲线。

按照[获取B样条曲线参数](/solidworks-api/geometry/get-bspline-parameters/)示例的指南从选定的边缘提取所需数据。

{% code-snippet { file-name: Macro.vba } %}