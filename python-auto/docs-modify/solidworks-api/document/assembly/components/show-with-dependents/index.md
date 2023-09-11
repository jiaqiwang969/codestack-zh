---
title: VBA Macro calls Show All Components command from SOLIDWORKS API
caption: Show All Components (Show With Dependents)
description: Example demonstrates how to call the Show With Dependents command for components or assembly using SOLIDWORKS API
image: assembly-show-with-dependents.png
labels: [assembly, components, show]
---
![装配体中的显示依赖项命令](assembly-show-with-dependents.png){ width=250 }

本示例演示了如何使用SOLIDWORKS API和Windows API调用“显示依赖项”命令，以一次性显示组件或装配体的所有组件。

如果没有选择组件，则宏将为所选装配体调用该命令。

{% code-snippet { file-name: Macro.vba } %}