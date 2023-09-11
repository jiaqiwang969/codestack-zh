---
layout: sw-tool
title: VBA macro to open referenced document of the drawing view
caption: Open Drawing View Referenced Document
description: VBA macro opens the document referenced by the selected drawing view in the referenced configuration and display state
image: ref-doc-display-state.svg
labels: [drawing,reference,display state]
group: Drawing
---
这个VBA宏执行类似于在所选的SOLIDWORKS图纸视图上执行**打开装配命令**的操作，但同时也激活与图纸视图相关联的引用显示状态。

![打开装配命令](open-assembly-command.png)

{% code-snippet { file-name: Macro.vba } %}