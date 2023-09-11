---
layout: sw-tool
title: Macro to copy path of SOLIDWORKS component to clipboard
caption: Copy Component Path
description: Macro copies the path of the selected component in assembly or drawing into the clipboard using SOLIDWORKS API
image: copy-component-path.png
labels: [path, clipboard, component]
group: Assembly
---
![在特征树中选择的组件](selected-component.png){ width=250 }

该宏使用SOLIDWORKS API将所选组件的完整路径复制到剪贴板。

* 组件可以在装配或绘图文档中选择
* 组件可以在特征树或图形区域中选择
    * 还可以选择组件实体（例如面或边）以获取组件的路径

{% code-snippet { file-name: Macro.vba } %}