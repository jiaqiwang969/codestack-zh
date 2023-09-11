---
layout: sw-tool
title: 使用SOLIDWORKS API选择相等弧的宏
caption: 选择相等弧
description: 使用SOLIDWORKS API查找并选择所有直径与输入弧相等的弧的VBA宏
image: selected-equal-arcs.png
labels: [草图,弧,圆,相等]
group: 草图
---
![在草图中选择相等弧](selected-equal-arcs.png){ width=350 }

这个VBA宏选择与预选输入草图弧相等大小的草图弧。只选择原始输入弧所在草图中的弧。该宏适用于活动和非活动草图。

## 选项

可以通过更改宏开头的常量的值来配置宏

~~~ vb
Const EPS As Double = 0.0000000001 '弧半径比较容差
~~~

{% code-snippet { file-name: Macro.vba } %}