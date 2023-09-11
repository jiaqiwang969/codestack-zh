---
layout: sw-tool
title: VBA宏打开图纸视图的引用文档
caption: 打开图纸视图引用文档
description: VBA宏打开所选图纸视图引用配置和显示状态的文档
image: ref-doc-display-state.svg
labels: [图纸,引用,显示状态]
group: 图纸
---
这个VBA宏执行类似于在所选的SOLIDWORKS图纸视图上执行**打开装配命令**的操作，但同时也激活与图纸视图相关联的引用显示状态。

![打开装配命令](open-assembly-command.png)

{% code-snippet { file-name: Macro.vba } %}