---
title: Get b-spline parameters from the selected edge using SOLIDWORKS API
caption: Get B-Spline Parameters
description: Get parameters of b-spline curve (dimension, order, periodicity, control and knot points) from the edge selected in the graphics view using SOLIDWORKS API
image: selected-bspline-edge.png
labels: [bspline, parameters, modeler, edge]
---
![选定的B样条边](selected-bspline-edge.png){ width=250 }

这个VBA示例从选定的B样条类型的边（例如从样条线段派生的边）中提取参数（维度、阶数、周期性、控制点和节点）。提取的数据可以在[SOLIDWORKS API的IModeler::CreateBsplineCurve](https://help.solidworks.com/2012/English/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModeler~CreateBsplineCurve.html)方法中使用，以构建相同几何形状的曲线。

数据以以下格式输出到VBA编辑器的即时窗口中：

~~~
属性：
 维度 值
 阶数 值
 控制点数量 值
 周期性 值
节点：
 值1
 ...
 值N
控制点：
 值1
 ...
 值N
~~~

{% code-snippet { file-name: Macro.vba } %}