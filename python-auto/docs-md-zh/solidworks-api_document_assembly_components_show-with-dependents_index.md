---
title: VBA宏调用SOLIDWORKS API中的显示所有组件命令
caption: 显示所有组件（显示依赖项）
description: 本示例演示了如何使用SOLIDWORKS API调用显示依赖项命令来一次性显示组件或装配体的所有组件
image: assembly-show-with-dependents.png
labels: [装配体, 组件, 显示]
---
![装配体中的显示依赖项命令](assembly-show-with-dependents.png){ width=250 }

本示例演示了如何使用SOLIDWORKS API和Windows API调用“显示依赖项”命令，以一次性显示组件或装配体的所有组件。

如果没有选择组件，则宏将为所选装配体调用该命令。

{% code-snippet { file-name: Macro.vba } %}