---
layout: sw-tool
title: Macro to make independent copy of the SOLIDWORKS component and copy drawing
caption: Make Independent With Drawing
description: VBA macro allows to make an independent copy of the selected component, update reference in assembly and copy associated drawing
image: make-independent-drawing.svg
labels: [make independent,drawing,component]
group: Assembly
---
此VBA宏模仿了SOLIDWORKS的**创建独立副本**功能，但还会额外复制并重命名与复制的零件或装配体组件相关联的文件。

![创建独立副本菜单命令](make-independent-menu.png)

此宏可以处理单个组件或多个选定的组件，但所有组件必须对应于同一个文件。

宏将复制相关的图纸并将其放置在与目标文件相同的位置，使用相同的名称。

## 注意事项

* 宏只会复制与源文件同名且位于相同文件夹中的图纸
* 如果目标图纸文件已存在，宏将不会覆盖它

{% code-snippet { file-name: Macro.vba } %}