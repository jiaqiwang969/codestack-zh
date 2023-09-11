---
layout: sw-tool
title: Macro to select equal arcs in the sketch using SOLIDWORKS API
caption: Select Equal Arcs
description: VBA macro to find and select all arcs with diameter equal to the input arc using SOLIDWORKS API
image: selected-equal-arcs.png
labels: [sketch,arc,circle,equal]
group: Sketch
---
![在草图中选择相等弧](selected-equal-arcs.png){ width=350 }

这个VBA宏选择与预选输入草图弧相等大小的草图弧。只选择原始输入弧所在草图中的弧。该宏适用于活动和非活动草图。

## 选项

可以通过更改宏开头的常量的值来配置宏

~~~ vb
Const EPS As Double = 0.0000000001 '弧半径比较容差
~~~

{% code-snippet { file-name: Macro.vba } %}