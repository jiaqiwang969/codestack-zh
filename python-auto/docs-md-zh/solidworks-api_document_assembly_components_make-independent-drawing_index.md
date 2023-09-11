---
layout: sw-tool
title: 宏以独立副本的形式创建SOLIDWORKS组件并复制图纸
caption: 以独立副本的形式创建并复制图纸
description: VBA宏允许创建所选组件的独立副本，更新装配体中的引用并复制相关的图纸
image: make-independent-drawing.svg
labels: [创建独立副本,图纸,组件]
group: 装配体
---
此VBA宏模仿了SOLIDWORKS的**创建独立副本**功能，但还会额外复制并重命名与复制的零件或装配体组件相关联的文件。

![创建独立副本菜单命令](make-independent-menu.png)

此宏可以处理单个组件或多个选定的组件，但所有组件必须对应于同一个文件。

宏将复制相关的图纸并将其放置在与目标文件相同的位置，使用相同的名称。

## 注意事项

* 宏只会复制与源文件同名且位于相同文件夹中的图纸
* 如果目标图纸文件已存在，宏将不会覆盖它

{% code-snippet { file-name: Macro.vba } %}