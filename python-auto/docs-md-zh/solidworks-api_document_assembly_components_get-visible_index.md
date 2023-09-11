---
title: 使用SOLIDWORKS API获取和选择装配中的所有可见组件
caption: 仅获取和选择可见组件
description: 使用SOLIDWORKS API获取和选择所有可见组件（未抑制和未隐藏）的VBA宏示例
image: components-tree.png
labels: [组件,抑制,隐藏,选择]
---
![在特征管理器树中选择的组件](components-tree.png){ width=350 }

这个VBA宏获取活动装配中所有可见（未抑制和未隐藏）组件的指针。使用多选的SOLIDWORKS API选择所有组件。

{% code-snippet { file-name: Macro.vba } %}