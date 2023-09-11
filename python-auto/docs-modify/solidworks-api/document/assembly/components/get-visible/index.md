---
title: Get and select all visible components in assembly using SOLIDWORKS API
caption: Get And Select Visible Components Only
description: VBA macro example to get and select all visible components (not suppressed and not hidden) using SOLIDWORKS API
image: components-tree.png
labels: [components,suppressed,hidden,select]
---
![在特征管理器树中选择的组件](components-tree.png){ width=350 }

这个VBA宏获取活动装配中所有可见（未抑制和未隐藏）组件的指针。使用多选的SOLIDWORKS API选择所有组件。

{% code-snippet { file-name: Macro.vba } %}