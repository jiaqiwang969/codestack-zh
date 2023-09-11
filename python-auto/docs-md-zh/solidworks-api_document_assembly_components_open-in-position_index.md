---
layout: sw-tool
title: 在新窗口中打开所选组件的位置
caption: 在位置中打开组件
description: VBA宏，将所选组件在当前装配视图中以相同位置的方式打开到单独的窗口中
image: open-in-position.svg
labels: [位置,组件]
group: 装配
---
这个VBA宏会将所有选定的组件在活动装配中以它们在原始SOLIDWORKS装配中的位置打开到各自的窗口中。

这个宏模拟了SOLIDWORKS工具栏中的“在位置中打开零件”命令，但允许同时打开多个选定的组件。

![在位置中打开零件命令](open-part-in-position-command.png){ width=250 }

{% code-snippet { file-name: Macro.vba } %}