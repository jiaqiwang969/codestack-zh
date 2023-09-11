---
title: 使用SOLIDWORKS API在尺寸中添加方程
caption: 在尺寸中添加方程
description: 本示例将修改所选尺寸的值，并将其设置为等于方程的值，使用SOLIDWORKS API。
image: sw-dimension-equation.png
labels: [尺寸, SOLIDWORKS API, 方程, 示例]
redirect-from:
  - /2018/03/solidworks-api-dimensions-add-equation-to-dim.html
---
本示例将使用SOLIDWORKS API修改所选尺寸的值，并将其设置为等于方程的值：

> sin(0.5) * 2 + (10 - 5)

![尺寸中的方程](sw-dimension-equation.png){ width=320 height=200 }

应使用[SOLIDWORKS API接口IEquationMgr](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IEquationMgr.html)来管理SOLIDWORKS文档中的方程。

{% code-snippet { file-name: Macro.vba } %}