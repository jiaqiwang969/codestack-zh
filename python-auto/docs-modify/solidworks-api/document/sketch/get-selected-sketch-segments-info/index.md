---
title: Get selected sketch segments info using SOLIDWORKS API
caption: Get Selected Sketch Segments Info
description: VBA macro to get the specific information from the selected sketch segments (line, arc, parabola, spline etc.) using SOLIDWORKS API
image: selected-sketch-segments.png
labels: [sketch segment,selection]
---

![在活动草图中选择的草图线段](selected-sketch-segments.png){ width=450 }

这个VBA宏演示了如何使用SOLIDWORKS API从选定的线段中提取特定的草图线段信息。

宏将遍历所有选定的对象并过滤草图线段。宏会识别线段的类型，并将指针转换为特定的子类型（如直线、样条、弧线、抛物线、文本等）。

信息将输出到VBA编辑器的即时窗口。

![草图线段的特定信息将打印到VBA编辑器的即时窗口](printed-sketch-segments-info.png){ width=350 }

{% code-snippet { file-name: Macro.vba } %}