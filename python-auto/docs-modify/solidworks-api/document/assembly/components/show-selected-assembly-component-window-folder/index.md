---
layout: sw-tool
title: SOLIDWORKS Macro shows selected assembly component in the Window folder
caption: Show Selected Assembly Component In The Window Folder
description: Example demonstrates how to open the folder of the selected component in the assembly in the Windows File Explorer
image: windows-folder-selected-component.svg
labels: [assembly, component, explorer, frame, macro, show in folder, solidworks, solidworks api, utility, vba]
group: Assembly
redirect-from:
  - /2018/03/show-selected-assembly-component-in.html
  - /solidworks-api/document/assembly/show-selected-assembly-component-window-folder
---

该宏演示了如何使用SOLIDWORKS API在Windows文件资源管理器中打开所选装配组件的文件夹。

所选组件的文件将在打开的窗口中预选。

该宏将产生类似于以下手动步骤的结果：

1. 在其自己的窗口中打开组件
2. 转到文件菜单
3. 从“最近打开的文件”中选择文件
4. 选择“在文件夹中显示”选项

![最近打开的文件菜单命令](open-recent.png){ width=320 height=69 }

如果没有选择任何组件，则将打开活动模型的路径。

观看[视频演示](https://youtu.be/9uZCecGg25I?t=266)

{% code-snippet { file-name: macro.vba } %}