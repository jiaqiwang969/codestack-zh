---
caption: 为草图分配随机颜色
title: 将随机颜色分配给文档中的草图的宏
description: VBA宏将随机颜色分配给SOLIDWORKS零件或装配体中的草图，并提供跳过已分配的草图和未吸收的草图的选项。

这个VBA宏将为所有活动零件或装配体的草图分配随机颜色。

宏可以配置为跳过已分配颜色的草图，并仅选择未吸收的草图（例如，未在其他特征中使用的草图）。

~~~vb
Const SKIP_ASSIGNED As Boolean = False '处理所有草图（包括已分配颜色的草图）
Const UNABSORBED_ONLY As Boolean = False '处理所有草图（吸收和未吸收的）
~~~

颜色将在特征外观级别上分配。

{% code-snippet { file-name: Macro.vba } %}

## 线条颜色

这是将颜色分配为线条颜色而不是特征外观的宏的替代版本。

此宏将为所有选定的草图或所有草图（如果没有选定的草图）分配随机颜色。仅当没有选定的草图时，才考虑**UNABSORBED_ONLY**选项。

{% code-snippet { file-name: SetLineColorMacro.vba } %}