---
layout: sw-tool
title: Open all selected components in positions in new windows
caption: Open Components In Positions
description: VBA macro to open each selected component in the assembly in the separate window in the same position they appear in the current assembly view
image: open-in-position.svg
labels: [position,component]
group: Assembly
---
这个VBA宏将在当前活动装配中以原始SOLIDWORKS装配中出现的相同位置，打开所有选定的组件。

这个宏模拟了SOLIDWORKS工具栏中的“在位置中打开零件”命令，但允许同时打开多个选定的组件。

![在位置中打开零件命令](open-part-in-position-command.png){ width=250 }

{% code-snippet { file-name: Macro.vba } %}