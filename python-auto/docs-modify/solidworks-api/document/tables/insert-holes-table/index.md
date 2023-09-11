---
caption: Insert Holes Table
title: Macro to insert holes table to SOLIDWORKS drawing
description: VBA macro demonstrates how to insert hole table for the specified entities using SOLIDWORKS API
image: holes-table.png
---
![孔表格](holes-table.png){ width=300 }

该宏演示了如何将孔表格插入到现有绘图中。

在运行宏之前，需要按照以下顺序预先选择输入对象。

1. 对应原点的顶点
2. 对应X轴的边
3. 对应Y轴的边
4. 包含孔的面

宏将清除选择并重新选择实体。

表格将使用默认模板插入到0,0坐标处。

> 注意，在您的情况下，您可能会使用不同的方法来检索实体的指针。

{% code-snippet { file-name: Macro.vba } %}