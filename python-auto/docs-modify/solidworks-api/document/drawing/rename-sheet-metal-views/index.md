---
layout: sw-tool
title: Rename flat pattern views with cut-list names VBA macro
caption: Rename Flat Pattern Views With Cut-List Names
description: VBA macro to rename all flat pattern views in the the active sheet after the respective cut-list names using SOLIDWORKS API
image: renamed-flat-pattern-drawing-view.png
labels: [rename view,cut list,flat pattern]
group: Drawing
---
![钣金零件的切割清单](切割清单名称.png){ width=250 }

钣金零件的切割清单名称可用于存储重要信息，例如零件编号。此VBA宏允许使用SOLIDWORKS API将活动绘图工作表中的所有钣金展开图视图重命名为相应的切割清单项名称。

![绘图视图重命名为切割清单后](重命名的展开图绘图视图.png){ width=250 }

{% code-snippet { file-name: Macro.vba } %}