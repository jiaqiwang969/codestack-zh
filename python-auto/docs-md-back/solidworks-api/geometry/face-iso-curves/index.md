---
title: Macro to create ISO curves for face using SOLIDWORKS API
caption: Create ISO Curves For Face
description: Example demonstrates how to find specified number of iso-curves in the u and v bounds of the selected face using SOLIDWORKS API
image: iso-curves-wire-body.png
labels: [curve, evaluate, geometry, macro, iso, uv, trimmed curve, vba]
---
![面的ISO曲线预览](iso-curves-wire-body.png){ width=300 }

该示例演示了如何使用SOLIDWORKS API在所选面的u和v边界中找到指定数量的ISO曲线。

* 选择面并运行宏
* 预览ISO曲线，宏执行停止
* 继续宏以清除预览

可以在以下代码段中更改u和v方向上的ISO曲线数量

~~~ vb
Dim vCurves As Variant
vCurves = GetIsoCurves(swFace, <u方向上的曲线数量>, <v方向上的曲线数量>)
~~~

可选地，宏允许在3D草图中创建曲线。

![为面的ISO曲线创建的草图](iso-curves-sketch.png){ width=300 }

可以通过在宏的开头将*CREATE_SKETCH*常量设置为*True*来启用此选项：

~~~ vb
Const CREATE_SKETCH As Boolean = True
~~~

**宏代码：**

{% code-snippet { file-name: Macro.vba } %}