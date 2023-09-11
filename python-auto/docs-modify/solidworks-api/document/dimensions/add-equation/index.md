---
title: Add equation to dimension using SOLIDWORKS API
caption: Add Equation To Dimension
description: Example will modify the value of the selected dimension and sets its value to be equal to the equation
image: sw-dimension-equation.png
labels: [dimension, solidworks api, equation, example]
redirect-from:
  - /2018/03/solidworks-api-dimensions-add-equation-to-dim.html
---
本示例将使用SOLIDWORKS API修改所选尺寸的值，并将其设置为等于方程的值：

> sin(0.5) * 2 + (10 - 5)

![尺寸中的方程](sw-dimension-equation.png){ width=320 height=200 }

应使用[SOLIDWORKS API接口IEquationMgr](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IEquationMgr.html)来管理SOLIDWORKS文档中的方程。

{% code-snippet { file-name: Macro.vba } %}