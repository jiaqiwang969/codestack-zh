---
title: Modify the definition of axis feature using SOLIDWORKS API
caption: Modify Axis Definition
description: VBA macro example to change the selection of the axis feature using SOLIDWORKS API
image: axis-definition.png
labels: [axis,definition]
---

![轴属性管理器页面](axis-definition.png){ width=250 }

这个VBA示例演示了如何使用SOLIDWORKS API修改轴特征的定义并更改选择。

* 首先选择要修改的目标轴特征
* 选择要设置为目标轴参考的对象，例如两个相交的平面、边等。

结果是所选对象（倒数第二个）将被分配给轴（第一个选择）。

{% code-snippet { file-name: Macro.vba } %}