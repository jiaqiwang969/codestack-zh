---
title: Select all suppressed components in the assembly using SOLIDWORKS API
caption: Select All Suppressed Components
description: VBA macro which runs the 'Component Selection - Select Suppressed' command in assembly document to select all assembly components in a batch
image: select-suppressed-components.png
labels: [command,suppressed,components]
---
这个VBA宏允许使用SOLIDWORKS和Windows API在活动的SOLIDWORKS装配中批量选择所有被压制的组件。

这将执行“组件选择”菜单中的“选择被压制”命令。

![选择被压制的组件的命令](select-suppressed-components.png){ width=500 }

与逐个遍历组件的方法相比，这是选择所有被压制组件的首选选项，因为它具有更好的性能优势。

{% code-snippet { file-name: Macro.vba } %}