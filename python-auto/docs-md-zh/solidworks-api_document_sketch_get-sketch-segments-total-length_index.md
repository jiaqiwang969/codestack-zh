---
标题：使用SOLIDWORKS API获取所选草图中线段的总长度
说明：使用SOLIDWORKS API计算所选草图中所有非构造几何线段的总长度的C#示例
图片：sketch-total-length.png
标签：[草图，长度]
---

![所选草图线段的总长度](sketch-total-length.png){ width=450 }

这是一个C#示例，用于计算使用SOLIDWORKS API在所选草图中所有线段的总长度。计算中将排除构造几何线段。

{% code-snippet { file-name: Program.cs } %}