---
title: Get the total length of segments in selected sketch using SOLIDWORKS API
caption: Get Total Length Of Sketch Segments
description: C# example to calculate total length of all non construction geometry sketch segments in the selected sketch using SOLIDWORKS API
image: sketch-total-length.png
labels: [sketch,length]
---

![所选草图线段的总长度](sketch-total-length.png){ width=450 }

这是一个C#示例，用于计算使用SOLIDWORKS API在所选草图中所有线段的总长度。计算中将排除构造几何线段。

{% code-snippet { file-name: Program.cs } %}