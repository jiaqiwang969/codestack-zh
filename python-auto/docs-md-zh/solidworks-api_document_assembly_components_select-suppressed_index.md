---
title: 使用SOLIDWORKS API选择所有被压制的组件
caption: 选择所有被压制的组件
description: 使用VBA宏在装配文档中批量运行“组件选择-选择被压制”命令以选择所有装配组件
image: select-suppressed-components.png
labels: [命令, 被压制, 组件]
---
这个VBA宏允许使用SOLIDWORKS和Windows API在活动的SOLIDWORKS装配中批量选择所有被压制的组件。

这将执行“组件选择”菜单中的“选择被压制”命令。

![选择被压制的组件的命令](select-suppressed-components.png){ width=500 }

与逐个遍历组件的方法相比，这是选择所有被压制组件的首选选项，因为它具有更好的性能优势。

{% code-snippet { file-name: Macro.vba } %}